# Задание 1

#### Метод реализации микрофронтендов:
Метод реализации микрофронтендов был выбран <i>Run Time</i> в гибридном подходе для использования преимуществ как серверной компоновки, так и клиентской. 
В нашей реализации клиент будет инициировать взаимодействие с сервером, отправляя HTTP-запросы. Сервер будет возвращать клиенту JSON с данными,
которые клиент будет парсить и передавать в React-компоненты для рендеринга. После этого данные могут изменяться разными микрофронтендами при взаимодействии с пользователем, 
используя глобальное состояние приложения.

Выбор метода <i>Run Time</i> был сделан по следующим причинам:
1. <b>Гибкость и динамичность:</b> Этот метод позволяет загружать и изменять компоненты приложения на лету, 
что повышает гибкость и позволяет быстрее реагировать на изменения требований.
2. <b>Меньшая зависимость от сборки:</b> В отличие от <i>Build Time</i>,
<i>Run Time</i> метод не требует повторной сборки всего приложения при изменении одного из микрофронтендов.
3. <b>Упрощенная интеграция и развертывание:</b> В случае развертывания новых функций или исправлений можно обновлять только соответствующие микрофронтенды 
без необходимости полного разворачивания всего приложения.
4. <b>Поддержка модульности и изоляции:</b> Микрофронтенды могут быть разработаны и развернуты независимо друг от друга, 
что улучшает модульность и изоляцию компонентов.

Таким образом, использование метода <i>Run Time</i> предоставляет значительные преимущества в гибкости, 
масштабируемости и простоте управления приложением.

#### Выбор фреймворка микрофронтендов:
Для создания микрофронтендов я использовал фреймворк <i>Webpack Module Federation</i>. 

Этот выбор обусловлен следующими причинами:

* <b>Общий код:</b> В проекте есть общий код, который будет использоваться несколькими микрофронтендами. 
Webpack Module Federation позволяет эффективно шарить (разделять) общий код между микрофронтендами, 
избегая дублирования и улучшая производительность.

* <b>Единый фреймворк:</b> Поскольку все микрофронтенды используют один и тот же фронтенд-фреймворк (React), 
Webpack Module Federation позволяет легко интегрировать их между собой без необходимости использования разных фреймворков.

* <b>Гибкость и масштабируемость:</b> <i>Webpack Module Federation</i> поддерживает динамическую загрузку модулей, 
что упрощает разработку и развертывание микрофронтендов, позволяя обновлять или заменять части приложения без перезагрузки всей страницы.

Список микрофронтендов состоит из выделенных в проекте доменов,
а также дополнительных микрофронтов для реализации архитектуры микрофронтов. 

Вот список микрофронтов:
* <b>host</b> - главное приложение, которое импортирует и рендерит компоненты из микрофронтендов.
* <b>auth</b> - отвечает за аутентификацию пользователей. Включает в себя все компоненты, 
необходимые для регистрации, входа в систему и проверки токенов пользователя.
* <b>profile</b> - отвечает за управление профилем пользователя. 
Здесь находятся компоненты для просмотра и редактирования информации профиля пользователя.
* <b>shared-components</b> - каталог содержит общие компоненты, которые используются в различных микрофронтендах. 
Сюда входят такие компоненты, как заголовки, подвали, формы, попапы, а также утилиты и контексты.
* <b>photo</b> - отвечает за работу с изоборажениями. 

Для внедрения инструмента нужно убедиться, что мы используем не ниже Webpack 5. 
Затем необходимо создать конфигурационный файл `webpack.config.js` для каждого из микрофронтендов, включая главное приложение. 
В этих конфигурационных файлах следует указать импортируемые и экспортируемые модули.

### Компоненты

**host:**
- `App` – основной компонент приложения   
- `ProtectedRoute` – компонент проверки авторизации 
- `InfoTooltip` – компонент работы с сообщениями 
- `Main` – основной компонент для отображения списка карточек изображений  

**auth:**
- `Login` – компонент для логина пользователя  
- `Register` – компонент регистрации пользователя

**profile:**
- `EditAvatarPopup` – компонент для редактирования аватарки пользователя  
- `EditProfilePopup` – компонент для редактирования профиля пользователя  

**shared:**
- `Footer` – подвал сайта  
- `Header` – шапка сайта 
- `PopupWithForm` – диалоговое окно сохранения

**photo:**
- `AddPlacePopup` – компонент добавления изображения  
- `ImagePopup` – компонент просмотра изображения   
- `Card` – компонент карточки с изображением

---

# Задание 2
Ссылка на диаграмму: https://drive.google.com/file/d/1UGVBsH1HYO3MskghCT9O41w5sFV0ir1T/view?usp=sharing