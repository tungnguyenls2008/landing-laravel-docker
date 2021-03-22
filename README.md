# ----------THIS ONE WORKS FINE-------------
# Landing Laravel - A Links Landing Laravel Application

This application creates a links landing page where you can share relevant links to an audience.
Links are initially imported from a `links.yml` file in the root of the application, and can be managed via Artisan commands (in the console / command-line).

## Managing Links
Links are initially imported from a `links.yml` file at the root of the repository. The seeds are only imported when the database is empty, so to not duplicate your links.

Link management is done via Artisan commands:

```shell
php artisan link:list
php artisan link:create
php artisan link:delete [LINK_ID]
```

## Development Workflow with Docker Compose
The application includes a Docker Compose setup that you can use for development. 
Please follow the [linked tutorial series](https://www.digitalocean.com/community/tutorial_series/how-to-build-a-links-landing-page-in-php-with-laravel-and-docker-compose) for more information about how to set up Docker and Docker Compose.

It's recommended that you fork this repository to your own Github account. 
Then, clone your forked repository so that you can make changes to the application.

To bring the environment up:

```shell
docker-compose up -d
```

Running Composer:

```shell
docker-compose exec app composer install
```

Setting up App Key:
```shell
docker-compose exec app php artisan key:generate
```

Running Migrations and Seeds:
```shell
docker-compose exec app php artisan migrate --seed
```

Then you should be able to access the application on `localhost:8080`.

Change the `links.yml` file to change the links that get seeded into the database by default, when the application is deployed.

To manage links, use `artisan`:

```shell
docker-compose exec app artisan link:list
```

This will list all links in the database. To add a new link, use `link:create`, and `link:delete LINK_ID` to delete links.


