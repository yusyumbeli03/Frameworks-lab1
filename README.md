# Лабораторная работа №1. Основы HTTP
- [Условие](#условие)
- [Выполнение заданий](#выполнение-заданий)
- [Использованные источники](использованные-источники)
## Условие
### Задание №1. Анализ HTTP-запросов
1. Зайдите на сайт http://sandbox.usm.md/login.
2. Откройте вкладку Network в инструментах разработчика браузера.
3. Введите неверные данные для входа (например, username: student, password: studentpass).
4. Проанализируйте запросы, которые были отправлены на сервер.
5. Ответьте на следующие вопросы:
- Какой метод HTTP был использован для отправки запроса?
- Какие заголовки были отправлены в запросе?
- Какие параметры были отправлены в запросе?
- Какой код состояния был возвращен сервером?
- Какие заголовки были отправлены в ответе?
6. Повторите шаги 3-5, введя верные данные для входа (username: admin, password: password).

 ### Задание №2. Составление HTTP-запросов

1.  Составьте `GET`-запрос к серверу по адресу `http://sandbox.com`, указав в заголовке `User-Agent` ваше имя и фамилию.
2.  Составьте `POST`-запрос к серверу по адресу `http://sandbox.com/cars`, указав в теле запроса следующие параметры:
    -   `make: Toyota`
    -   `model: Corolla`
    -   `year: 2020`
3.  Составьте `PUT`-запрос к серверу по адресу `http://sandbox.com/cars/1`, указав в заголовке `User-Agent` ваше имя и фамилию, в заголовке `Content-Type` значение `application/json` и в теле запроса следующие параметры: `json { "make": "Toyota", "model": "Corolla", "year": 2021 }`
4.  Напишите один из возможных вариантов ответа сервера следующий запрос. `http POST /cars HTTP/1.1 Host: sandbox.com Content-Type: application/json User-Agent: John Doe model=Corolla&make=Toyota&year=2020` Предположите ситуации, когда сервер может вернуть HTTP-коды состояния 200, 201, 400, 401, 403, 404, 500.

### Задание №3. Дополнительное задание. HTTP_Quest

> TIP
>
> Пройдите квест отправляя запросы на сервер.

1.  Отправьте `POST`-запрос на сервер по адресу `http://sandbox.usm.md/quest`, указав в заголовке User-Agent вашу фамилию и имя (Например `User-Agent: John Doe`).

```
POST /quest HTTP/1.1
Host: sandbox.usm.md
User-Agent: John Doe

```

curl:

```
curl -X POST http://sandbox.usm.md/quest -H "User-Agent: John Doe"

```

1.  Следуйте инструкциям на сервере, выполняя их по порядку.
2.  В конце квеста Вам будет показано секретное слово, которое Вы должны будете предоставить в отчете.

*Примечание к заданию 3*:

1.  Используйте инструмент `curl`, `postman` или любой другой инструмент для отправки запросов.
2.  Вы можете начинать квест заново, выполнив первый шаг.
 ## Выполнение заданий
 ### 1. Задание №1. Анализ HTTP-запросов  
 ![alt text](screens/{D792B0B4-E6AC-4A8C-A337-27BB7BDB06C2}.png)

-   Какой метод HTTP был использован для отправки запроса?  
`POST`
-   Какие заголовки были отправлены в запросе?  
![alt text](screens/{186AC58B-FF38-4C7A-8689-5BFB54244459}.png)

-   Какие параметры были отправлены в запросе?  
![alt text](screens/{707DCBB5-84AF-4C98-8A37-EA0D360B7C83}.png)

-   Какой код состояния был возвращен сервером?  
![alt text](screens/image.png)

-   Какие заголовки были отправлены в ответе?  
![alt text](screens/{DD7C26A5-C4B9-421B-9F1B-5EFDC9A7319C}.png)

2. Попытка с верными данными  
![alt text](screens/{88877BC9-C017-4A60-8DED-DF0134EB05BE}.png)  

-   Какой метод HTTP был использован для отправки запроса?  
`POST`
-   Какие заголовки были отправлены в запросе?  
![alt text](screens/{5303E9A7-F6BC-40C5-91A6-998361650417}.png)

-   Какие параметры были отправлены в запросе?  
![alt text](screens/{8F8070E5-3A8E-4E3D-B9F4-B2BACA357DDD}.png)

-   Какой код состояния был возвращен сервером?    
![alt text](screens/{1E8A7A24-E27E-4B25-BCD7-DA0448BCF49C}.png)

-   Какие заголовки были отправлены в ответе?  
![alt text](screens/{C6EA7FBD-8D55-4826-8F1C-762E9016D25E}.png)

## Задание №2. Составление HTTP-запросов

`GET`
```http
GET / HTTP/1.1
Host: sandbox.com
User-Agent: Iusiumbeli Aliona
```

`POST`
```HTTP
POST /cars HTTP/1.1
Host: sandbox.com

make=Toyota&model=Corolla&year=2020
```

`PUT`
```http
PUT /cars/1 HTTP/1.1
Host: sandbox.com
Content-Type: application/json
User-Agent: Iusiumbeli Aliona

{
    "make": "Toyota",
    "model": "Corolla",
    "year": 2021
}
```
4. Возможный вариант ответа  
```http
HTTP/1.1 201 Created
Location: /cars/1
Content-Type: application/json

{
    "id": 1,
    "make": "Toyota",
    "model": "Corolla",
    "year": 2024
}
```

-   Какой метод HTTP был использован для отправки запроса?
-   **200 OK** --- успешный запрос, сервер возвращает запрашиваемый ресурс. 
> Например, при успешном выполнении GET-запроса.
-   **201 Created** --- ресурс успешно создан. 
> Например, POST-запрос на создание нового автомобиля на сервере.
-   **400 Bad Request** --- запрос неверный или содержит ошибки. 
> Например, в POST-запросе указаны некорректные параметры.
-   **401 Unauthorized** --- попытка доступа без авторизации. 
> Например, если запрос требует аутентификации, но заголовок авторизации отсутствует.
-   **403 Forbidden** --- доступ запрещён, даже если авторизация прошла. 
> Например, у пользователя нет прав на выполнение действия.
-   **404 Not Found** --- запрашиваемый ресурс не найден. 
> Например, если отправлен запрос на несуществующий URL.
-   **500 Internal Server Error** --- внутренняя ошибка сервера. 
> Например, если сервер не смог обработать запрос из-за сбоя в работе приложения.

## Задание №3. Дополнительное задание. HTTP_Quest
1. 
![alt text](screens/{6C164DF6-2078-4A54-B8A7-F636D1954544}.png)
2. 
```cmd
curl -X POST http://sandbox.usm.md/quest/login  -H "Authorization: Bearer ABQePR0IIAAfHWkgAT0HCyM="
```
![alt text](screens/{C5A83EA8-DC60-481B-94D9-C55967165228}.png)

3. 
```cmd
curl -X PUT http://sandbox.usm.md/quest/login  -H "Authorization: Bearer ABQePR0IIAAfHWkgAT0HCyM=" -d "age=21"
```

![alt text](screens/{7D9C0811-BC14-4BF6-968E-8442ECB5C97A}.png)

4. 
```cmd
curl -X GET http://sandbox.usm.md/quest/secret?token=ABQePR0IIAAfHRIyCA8LHQdJQlF7V15mUV16XQ==
```
![alt text](screens/{0834486B-C27F-42FF-8522-ECFC68738CD8}.png)

-  Секретное слово : `IDkcHxAkAQAgCFQ1CUgGIg5bV3g=`

## Использованные источники

[https://github.com/MSU-Courses/frameworks-for-web-development/blob/main/ru/01_http_basics/01_04_curl.md](https://github.com/MSU-Courses/frameworks-for-web-development/blob/main/ru/01_http_basics/01_04_curl.md)