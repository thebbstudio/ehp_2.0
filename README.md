__Структура проекта__
Проект можно разделить на три смысловые части:

- *База данных*
- *Фронтенд*
- *Бекент*


__База данных__
Как требовалось в задании, я не использовал ORM и делал запросы к БД через sql и connection.cursor() (web.view, api.view).
Описание таблиц сделано в файле api.models. Я не до конца понял, как реализуются категории, поэтому создал для них таблицу и ссылаюсь через внешний ключ в таблице api_employee для редактирования списка категорий можно использовать *админ панель*
Детальное описание в файле api.models

__Фронтенд__
Страницы можно разделить на две категории:
- Для работы с *Сотрудниками*
- Для работы с *Должностями*

При открытии сайта происходит автоматический редирект на страницу с таблицей сотрудников. Во вьюхе делаю запрос на получение сотрудников, после чего передаю список в HTML шаблон, там с помощью цикла вывожу список сотрудников, добавляя каждой строке кнопки для редактирвания и удаления записи. 

На данной странице можно перейти на форму добавления кликнув на плюсик. Форма создаётся с помощью встоенного фунционала джанго. Для редактирования существующего объекта необходимо в конструктор формы передать класс. Для удаления кликаем на корзину и посылвается запрос на сервер.

**Итог:** 

для просмотра, создания, удаления и редактирования *данных сотрудника* и *должности* можно было использовать два HTML шаблона:
- Шаблон принимающий класс формы готовый к применению для создания и удаления этих двух сущностей
- Шаблон для вывода таблицы, который принимает список столбцов, который можно создать циклом, и вывод строк тоже циклом. 

Я решил не мудрить и создал по три шаблона. Хотя данное решение позволило более удобно контролировать вывод данных исключая ситуаций например при оборачивании таблицы в div нужно обернуть так же в бругом шабоне.

**JavaScript**
JS занимается отправкой и обработкой запроса на удаление. Появляется уведомление и происходит удаление объекта из таблице при хорошем исходе. Так же JS занимается навигацией на сайте перенаправлая пользователя при назании на кнопку редактирования. Навигация так же происходит с помощью ссылок.

__Бекенд__

Я создал два приложения для обработки API и запросов на получение страниц(WEB).

В папке API хранятся:
- Модели базы данны,
- Роутинг запросов к API,
- Настройки админ панели,
- Представления для обаботки запросок к API.

В папке Web хранятся:
- Формы создания и редактирования,
- Представления для обработки запросов на получение страниц,
- В Urls.py роутинг.
*ничего необычного*  
