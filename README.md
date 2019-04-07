# Symfony Messenger Presentation

This here is the source code used in Dominik Najberg's presenation about the Symfony Messenger.

Please follow branch names to see the steps. You may look into this readme file for additional explanations.

## RabbitMQ Docker Image

```
git clone git@github.com:micahhausler/rabbitmq-compose.git
cd rabbitmq-compose
sudo docker-compose up
```
------------------
You can log in to your RabbitMQ through:
http://localhost:15672/

Login: rabbitmq
Password: rabbitmq

## Step 1 (No Handler exception)

* SendMessage created
* Simple controller so you can open http://127.0.0.1:8000 to test the changes

## Step 2 (Handler added)

* Added a handler for the SendMessage object

## Step 3 (Multiple Buses)

* Two buses available now
* SendNotificationHandler implements MessageSubscriberInterface
* Autowiring configured

## Step 4 (Custom Middleware)

* Added the AuditMiddleware

## Step 5 (Custom Stamp)

* Added the AuditStamp custom stamp
* Correlation ID

## Step 6 (Transport)

* RabbitMQ

Remember to run your RabbitMQ docker image. Also, run the Worker:

```
bin/console messenger:consume-messages amqp -b messenger.bus.commands
```

## Step 7 (Custom Transport)

* Custom Transport

Run *composer install* due to the Guzzle Client dependency.

## Useful links
* [Symfony Messenger](https://symfony.com/doc/current/components/messenger.html)
* [Dominik Najberg - contact to this presentation's author](https://www.linkedin.com/in/dominik-najberg/)