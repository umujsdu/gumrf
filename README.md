## Старт

#### 1) Создать образ

    docker-compose build

##### 2) Запустить контейнер

    docker-compose up
    
##### 3) Перейти по адресу

    http://127.0.0.1:8000/api/v1/swagger/

## Разработка с Docker

##### 1) Сделать форк репозитория

##### 2) Клонировать репозиторий

    git clone ссылка_сгенерированная_в_вашем_репозитории

##### 3) В корне проекта создать .env.dev

    DEBUG=1
    SECRET_KEY=fdsadqw3f32wg<43g3hv$%#@%F$F$$F$F
    DJANGO_ALLOWED_HOSTS=localhost 127.0.0.1 [::1]
    
    # Data Base
    POSTGRES_DB=gumrf
    POSTGRES_ENGINE=django.db.backends.postgresql
    POSTGRES_DATABASE=gumrf
    POSTGRES_USER=gumrf_user
    POSTGRES_PASSWORD=gumrf_pass
    POSTGRES_HOST=gumrf-db
    POSTGRES_PORT=5432
    DATABASE=postgres

    # Email
    DEFAULT_FROM_EMAIL=your@your.com
    EMAIL_USE_TLS=True
    EMAIL_HOST=your_smtp
    EMAIL_HOST_USER=your@your.com
    EMAIL_HOST_PASSWORD=pass
    EMAIL_PORT=587
    
##### 4) Создать образ

    docker-compose build

##### 5) Запустить контейнер

    docker-compose up
    
##### 6) Применить миграции 

    docker exec -it gumrf_gumrf_back_1 python manage.py migrate 

##### 7) Создать суперюзера

    docker exec -it gumrf_gumrf_back_1 python manage.py createsuperuser
                                                        
##### 8) Если нужно очистить БД

    docker-compose down -v

##### 9) Для авторизации необходимо с помощью hanlder-а auth/jwt/create получить access token. Далее в swagger файле нажать на кнопку Authorize и вставить данный токен с префиксом JWT

    JWT <your-token-goes-here>
