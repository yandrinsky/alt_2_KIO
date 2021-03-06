# Пример разработки задачи конкурса КИО

Чтобы разработать собственную задачу для конкурса КИО, клонируйте репозиторий, запустите

```
npm install
npm run compile
```

После этого в каталоге `dist` появятся html файлы с задачами.

Другие команды: `npm run compile-prod` компилирует production версию в каталог `dist-prod`. `npm run watch` компилирует проект в каталог `dist` в режиме отладки, запускает процесс, который следит за изменениями исходных файлов, и автоматически перекомпилирует их при изменении.

## Содержимое репозитория

```
├── dist                                каталог с результатами компиляции в режиме отладки
├── dist-prod                           каталог с результатами компиляции для выкладывания
├── kio_test_box                        каталог вспомогательных файлов и библиотек, включая KioApi
├── package.json                        описание node.js проекта
├── package-lock.json                   версии установленных библиотек
├── tasks                               каталог исходников задач
│   ├── collatz_es_next                 версия задачи 3x+1 на последней версии JS
│   │   ├── collatz_es_next.js
│   │   ├── collatz_es_next-resources
│   │   │   └── collatz_conjecture.png 
│   │   └── collatz.scss
│   ├── collatz_js                      версия задачи 3x+1 на JS, работающем в браузерах
│   │   ├── collatz_js.js              
│   │   ├── collatz_js-resources
│   │   │   └── collatz_conjecture.png
│   │   └── collatz.scss
│   ├── collatz_ts                      версия задачи 3x+1 на TypeScript
│   │   ├── collatz.scss
│   │   ├── collatz_ts-resources
│   │   │   └── collatz_conjecture.png
│   │   └── collatz_ts.ts
│   ├── KioApi.d.ts                     описание типов KioApi для кода на TypeScript
│   └── task.html                       HTML шаблон для тестирования задач
├── tsconfig.json                       Настройки компилятора TypeScript
└── webpack.config.js                   Настройки сборщика проекта webpack

```

Каталоги `collatz_js`, `collatz_es_next`, `collatz_ts` содержат один и тот же код на разных языках. В файле `collats_js\collats_js.js` есть подробные комментарии. На других языках комментариев нет, чтобы не повторяться.


## Возможные проблемы

1. Команда `npm run watch` просматривает каталог `tasks` и компилирует каждый подкаталог в нём как отдельную задачу. Поэтому при добавлении новой задачи нужно остановить и перезапустить `npm run watch`.
2. Запустить в браузере HTML файл напрямую из каталогов `dist` или `dist-prod` скорее всего не получится из-за невозможности совершить CORS запрос для проверки доступа к png файлу на диске. Надо просматривать файлы с локального веб-сервера (встроен в IntelliJ IDEA Ultimate, или можно запустить отдельно, например [NPM Live Server](https://www.npmjs.com/package/live-server)). Еще можно настроить свой браузер на игнорирование проблемы [https://stackoverflow.com/a/41980210](https://stackoverflow.com/a/41980210)
