# api_final
Api для yatube основан на JWTAuthentication.<br>
Он может принимать анонимные запросы для получиения всех публикаций, комментариев, сообществ.<br>
А также запросы на конкретный обьект.<br>
Чтобы обработать запросы на создание публикаций и комментариев, 
пользователю необходимо пройти аутентификацию.<br>
Аутентифицированный пользователь авторизован на изменение и удаление своего контента;
в остальных случаях доступ предоставляется только для чтения. 
При попытке изменить чужие данные возвращается код ответа 403 Forbidden.<br>

Также в проекте описана модель Follow.<br>
он принимает два метода:<br> 
GET — возвращает все подписки пользователя, сделавшего запрос. 
Возможен поиск по подпискам по параметру search.<br>
POST — подписать пользователя, сделавшего запрос на пользователя, переданного в теле запроса.
При попытке подписаться на самого себя, пользователь должен получить информативное 
сообщение об ошибке. Проверка осуществляется на уровне API.<br>


**Стеки использованых технологий:**<br>
Python==3.8 <br>
Django==3.2.16 <br>
pytest==6.2.4 <br>
pytest-pythonpath==0.7.3 <br>
pytest-django==4.4.0 <br>
djangorestframework==3.12.4 <br>
djangorestframework-simplejwt==4.7.2 <br>
django-filter==23.2 <br>
Pillow==9.3.0 <br>
PyJWT==2.1.0 <br>
requests==2.26.0 <br> 

**Как запустить проект:**

Клонировать репозиторий и перейти в него в командной строке:<br>
windows / linux


`git clone https://github.com/saikal12/api_yatube.git`

`cd yatube_api`

Cоздать и активировать виртуальное окружение:<br>
Windows<br>`
pyhon -m venv venv `<br>

`
venv\Scripts\activate.bat`<br>Linux/macOS<br>

`python3 -m venv venv`<br>
`
sourse venv/bin/activate`

Обновить PIP:<br>
Windows<br>`python -m pip install --upgrade pip`<br>Linux/macOS<br>
`python3 -m pip install --upgrade pip`

Установить зависимости из файла requirements.txt:<br>
`pip install -r requirements.txt`<br>
`pip install -r requirements.txt`<br>

Выполнить миграции:

Windows<br>`
python manage.py makemigrations`<br>`
python manage.py migrate`

Linux/macOS

`python3 manage.py makemigrations`<br>`
python3 manage.py migrate`

Запустить проект:

Windows

`python manage.py runserver`

Linux/macOS

`python3 manage.py runserver`



**Для взаимодействия с ресурсами описаны и настроены такие эндпоинты:**<br>
-api/v1/posts/ (GET, POST): получаем список всех постов или создаём новый пост.<br>
-api/v1/posts/{post_id}/ (GET, PUT, PATCH, DELETE): получаем, редактируем или удаляем пост по id.<br>
-api/v1/groups/ (GET): получаем список всех групп.<br>
-api/v1/groups/{group_id}/ (GET): получаем информацию о группе по id.<br>
-api/v1/posts/{post_id}/comments/ (GET, POST): получаем список всех комментариев поста с id=post_id или создаём новый, указав id поста, который хотим прокомментировать.<br>
-api/v1/posts/{post_id}/comments/{comment_id}/ (GET, PUT, PATCH, DELETE): получаем, редактируем или удаляем комментарий по id у поста с id=post_id.<br>
-api/v1/follow/ (GET): Возвращает все подписки пользователя, сделавшего запрос<br>
-api/v1/follow/ (POST): Подписка пользователя от имени которого сделан запрос на пользователя переданного в теле запроса<br>

