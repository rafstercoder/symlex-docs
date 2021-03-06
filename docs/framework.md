# Getting Started

## Command-line Application ##

Make sure you have PHP 7.1+ and [Composer](https://getcomposer.org/) installed on your system.

**Step 1:** Run `composer` to create a new project from our example:

    composer create-project symlex/stream-sampler myapp

**Step 2:** Use `app/console` to execute commands: 

    cd myapp
    app/console sample -i internal -s 10

Repository: https://github.com/symlex/stream-sampler

## Web Applications ##

Before you start, make sure you have PHP 7.1+, [Composer](https://getcomposer.org/) and [Docker](https://www.docker.com/) installed on your system 
([howto](https://docs.symlex.org/en/latest/osx/) for Mac OS X). 
Instead of using Docker, you can also setup your own runtime environment based on the existing 
Dockerfiles (not recommended).

### Simple REST API ###

**Step 1:** Run `composer` to create a new project:

```
composer create-project symlex/rest-api myapp
```

**Step 2:** Start nginx and PHP using `docker-compose`:

```
cd myapp
docker-compose up
```

**Step 3:** Open http://localhost:8088/example/123 in a browser ([source](https://github.com/symlex/rest-api/blob/master/src/Controller/ExampleController.php)).

Repository: https://github.com/symlex/rest-api

### Single-page Application ###

**Step 1:** Run `composer` to create a new project:

```
composer create-project symlex/symlex myapp
```

**Step 2:** Start nginx, PHP and MySQL using `docker-compose`:

```
cd myapp
docker-compose up
```

!!! info
    This docker-compose configuration is for testing and development purposes only. On OS X, the current release of 
    Docker is [really slow](https://twitter.com/lastzero/status/829191426391027712) in executing PHP from the host's file system.

**Step 3:** Let [Phing](https://www.phing.info/) initialize the database and build the front-end components for you:

```
docker-compose exec php sh
bin/phing dev
```

!!! tip
    You can also use this approach to execute other commands later (see `build.xml`). Alternatively, you can 
    install npm and Yarn locally and link "db" to 127.0.0.1 in /etc/hosts to run them directly on your host.

Repository: https://github.com/symlex/symlex

#### Web UI ####

After successful installation, open the site at http://localhost:8081/ and log in as `admin@example.com` using the 
password `passwd`. If you add `localhost-debug` to your /etc/hosts and access the site with that, it will load in debug
mode (you'll see a stack trace and other debug information on the error pages).

![Screenshot](img/login.jpg)

#### MailHog ####

The [mailhog](https://github.com/ian-kent/MailHog) user interface is available at http://localhost:8082/. It can be used
to receive and view mails automatically sent by the system, e.g. when new users are created.

![Screenshot](img/mailhog.jpg)
