# Dupray Technical Test 2025

## Installation

Follow the instructions below to set up a local [Laravel](https://laravel.com) development environment that is fully containerized within Docker. The commands below must be run from a Unix/Linux environment. If you are running Microsoft Windows, you should already have the [Windows Subsystem for Linux (WSL)](https://learn.microsoft.com/en-us/windows/wsl/install) installed and configured on your computer. This is beyond the scope of the project, so you must set this up on your own.

Download and install [Docker Desktop](https://www.docker.com/products/docker-desktop) if you do not have it installed on your computer. You do not need to create a Docker account. You can skip Docker's account creation if it prompts you.

Clone the repository to your computer.

Install the project's Composer dependencies using the Docker command below. This will download and run a temporary Docker container that will install the Composer packages for the project.

```
docker run --rm \
    -u "$(id -u):$(id -g)" \
    -v "$(pwd):/var/www/html" \
    -w /var/www/html \
    laravelsail/php84-composer:latest \
    composer install --ignore-platform-reqs
```

Make a copy of the `.env.example` file and rename the copied file to `.env`. You don't need to change any environment variables. The default values will get you up and running.

Run the following command to initialize the Docker environment: `./vendor/bin/sail up -d`. This initialization process will download and configure a fully containerized linux environment with PHP, MySQL, Redis, Mailpit, Meilisearch and Selenium. Please be patient as this may take a few minutes. You can refer to the `docker-compose.yml` for more details on the Docker configuration.

Generate your Laravel app key using the following commands: `./vendor/bin/sail artisan key:generate`.

Install the Node dependencies using the following command: `./vendor/bin/sail npm ci`.

Visit the site in your browser at [http://localhost](http://localhost). You should see the default Laravel page which indicates that your environment is working correctly.

Start developing.

## Useful Commands

Launch the Docker container: `./vendor/bin/sail up -d`. The `-d` parameter runs the container in headless (background) mode so you can continue using the command line.

Shut down the Docker container: `./vendor/bin/sail down`.

Check the Docker container status: `./vendor/bin/sail ps`.
