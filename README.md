# Docker-compose Build example for `hyperf` PHP framework
- The `hyperf` service will start automatically when docker starts.
- Easily Implement Free SSL Certification

## Use composer via workspace container
```shell
cp .env.example .env
docker-compose up -d workspace
docker-compose exec workspace bash

# in the workspace container
composer create-project hyperf/hyperf-skeleton ./
# composer install -vvv
```

## Start the web service
```shell
docker network create caddy
docker-compose up -d web
```

open http://localhost:9501
#### Expect result
```json
{"method":"GET","message":"Hello Hyperf."}
```

## Automatically Implement Free SSL certificate via caddy
Please complete your DNS configuration through your domain name provider settings page in advance.

### Set your domain in the .env configuration
```dotenv
# For example
SITE_VIP=www.your_domain.com
# If local DNS ( http )
# SITE_VIP=http://www.your_domain.com
```

### recreate container
```dotenv
docker-compose up -d web caddy
```
see the result: https://www.your_domain.com

## See Also
https://github.com/lucaslorentz/caddy-docker-proxy <br/>
https://caddyserver.com/ <br/>
https://github.com/hyperf/hyperf-docker/ <br/>