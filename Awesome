# Стиль написания кода на JavaScript для Uprock: Перевод и расширение [Airbnb JavaScript Style Guide](https://github.com/airbnb/javascript)

*Наиболее разумный подход к JavaScript*


## <a name='TOC'>Оглавление</a>

  1. [Типы](#types)
  1. [Объекты](#objects)
  1. [Массивы](#arrays)
  1. [Строки](#strings)
  1. [Функции](#functions)
  1. [Свойства](#properties)
  1. [Переменные](#variables)
  1. [Области видимости](#hoisting)
  1. [Условные выражения и равенства](#conditionals)
  1. [Блоки кода](#blocks)
  1. [Комментарии](#comments)
  1. [Пробелы](#whitespace)
  1. [Запятые](#commas)
  1. [Точки с запятой](#semicolons)
  1. [Приведение типов](#type-coercion)
  1. [Соглашение об именовании](#naming-conventions)
  1. [Геттеры и сеттеры](#accessors)
  1. [Конструкторы](#constructors)
  1. [События](#events)
  1. [Модули](#modules)
  1. [jQuery](#jquery)
  1. [Совместимость с ES5](#es5)
  1. [Тестирование](#testing)
  1. [Быстродействие](#performance)
  1. [Ресурсы](#resources)
  1. [В реальном мире](#in-the-wild)
  1. [Переводы](#translation)
  1. [Лицензия](#license)

## <a name='types'>Типы</a>

  - **Простые типы**: Когда вы взаимодействуете с простым типом, вы взаимодействуете непосредственно с его значением в памяти.

    + `string`
    + `number`
    + `boolean`
    + `null`
    + `undefined`

    ```javascript
    var foo = 1,
        bar = foo;

    bar = 9;

    console.log(foo, bar); // => 1, 9. foo не изменился
    ```
  - **Сложные типы**: Когда вы взаимодействуете со сложным типом, вы взаимодействуете с ссылкой на его значение в памяти.

    + `object`
    + `array`
    + `function`

    ```javascript
    var foo = [1, 2],
        bar = foo;

    bar[0] = 9;

    console.log(foo[0], bar[0]); // => 9, 9.
    ```

    **[[⬆]](#Оглавление)**

## <a name='objects'>Объекты</a>

  - Для создания объекта используйте фигурные скобки. Не создавайте объекты через конструктор `new Object`.

    ```javascript
    // плохо
    var item = new Object();

    // хорошо
    var item = {};
    ```

  - Не используйте [зарезервированные слова](http://es5.github.io/#x7.6.1) в качестве ключей объектов. Они не будут работать в IE8. [Подробнее](https://github.com/airbnb/javascript/issues/61)

    ```javascript
    // плохо
    var superman = {
      default: { clark: 'kent' },
      private: true
    };

    // хорошо
    var superman = {
      defaults: { clark: 'kent' },
      hidden: true
    };
    ```

  - Не используйте ключевые слова (в том числе измененные). Вместо них используйте синонимы.

    ```javascript
    // плохо
    var superman = {
      class: 'alien'
    };

    // плохо
    var superman = {
      klass: 'alien'
    };

    // хорошо
    var superman = {
      type: 'alien'
    };
    ```
    **[[⬆]](#Оглавление)**

## <a name='arrays'>Массивы</a>

  - Для создания массива используйте квадратные скобки. Не создавайте массивы через конструктор `new Array`.

    ```javascript
    // плохо
    var items = new Array();

    // хорошо
    var items = [];
    ```

  - Если вы не знаете длину массива, используйте Array::push.

    ```javascript
    var someStack = [];


    // плохо
    someStack[someStack.length] = 'abracadabra';

    // хорошо
    someStack.push('abracadabra');
    ```

  - Если вам необходимо скопировать массив, используйте Array::slice. [jsPerf](http://jsperf.com/converting-arguments-to-an-array/7)

    ```javascript
    var len = items.length,
        itemsCopy = [],
        i;

    // плохо
    for (i = 0; i < len; i++) {
      itemsCopy[i] = items[i];
    }

    // хорошо
    itemsCopy = items.slice();
    ```

  - Чтобы скопировать похожий по свойствам на массив объект (например, NodeList или Arguments), используйте Array::slice.

    ```javascript
    function trigger() {
      var args = Array.prototype.slice.call(arguments);
      ...
    }
    ```

    **[[⬆]](#Оглавление)**


## <a name='strings'>Строки</a>

  - Используйте одинарные кавычки `''` для строк.

    ```javascript
    // плохо
    var name = "Боб Дилан";

    // хорошо
    var name = 'Боб Дилан';

    // плохо
    var fullName = "Боб " + this.lastName;

    // хорошо
    var fullName = 'Дилан ' + this.lastName;
    ```

  - Строки длиннее 80 символов нужно разделять, выполняя перенос через конкатенацию строк.
  - Осторожно: строки с большим количеством конкатенаций могут отрицательно влиять на быстродействие. [jsPerf](http://jsperf.com/ya-string-concat) и [Обсуждение](https://github.com/airbnb/javascript/issues/40)

    ```javascript
    // плохо
    var errorMessage = 'Эта сверхдлинная ошибка возникла из-за белой обезъяны. Не говори про обезъяну! Не слушай об обезьяне! Не думай об обезъяне!';

    // плохо
    var errorMessage = 'Эта сверхдлинная ошибка возникла из-за белой обезъяны. \
    Не говори про обезъяну! Не слушай об обезьяне! \
    Не думай об обезъяне!';

    // хорошо
    var errorMessage = 'Эта сверхдлинная ошибка возникла из-за белой обезъяны. ' +
      'Не говори про обезъяну! Не слушай об обезьяне! ' +
      'Не думай об обезъяне!';
    ```

  - Когда строка создается программным путем, используйте Array::join вместо объединения строк. В основном для IE: [jsPerf](http://jsperf.com/string-vs-array-concat/2).

    ```javascript
    var items,
        messages,
        length,
        i;

    messages = [{
        state: 'success',
        message: 'Это работает.'
    },{
        state: 'success',
        message: 'Это тоже.'
    },{
        state: 'error',
        message: 'А я томат.'
    }];

    length = messages.length;

    // плохо
    function inbox(messages) {
      items = '<ul>';

      for (i = 0; i < length; i++) {
        items += '<li>' + messages[i].message + '</li>';
      }

      return items + '</ul>';
    }

    // хорошо
    function inbox(messages) {
      items = [];

      for (i = 0; i < length; i++) {
        items[i] = messages[i].message;
      }

      return '<ul><li>' + items.join('</li><li>') + '</li></ul>';
    }
    ```

    **[[⬆]](#Оглавление)**


## <a name='functions'>Функции</a>

  - Объявление функций:

    ```javascript
    // объявление анонимной функции
    var anonymous = function() {
      return true;
    };

    // объявление именованной функции
    var named = function named() {
      return true;
    };

    // объявление функции, которая сразу же выполняется (замыкание)
    (function() {
      console.log('Если вы читаете это, вы открыли консоль.');
    })();
    ```
  - Никогда не объявляйте функцию внутри блока кода — например в if, while, else и так далее. Единственное исключение — блок функции. Вместо этого присваивайте функцию уже объявленной через `var` переменной. Условное объявление функций работает, но в различных браузерах работает по-разному.
  - **Примечание** ECMA-262 устанавливает понятие `блока` как списка операторов. Объявление функции (не путайте с присвоением функции переменной) не является оператором. [Комментарий по этому вопросу в ECMA-262](http://www.ecma-international.org/publications/files/ECMA-ST/Ecma-262.pdf#page=97).

    ```javascript
    // плохо
    if (currentUser) {
      function test() {
        console.log('Плохой мальчик.');
      }
    }

    // хорошо
    var test;
    if (currentUser) {
      test = function test() {
        console.log('Молодец.');
      };
    }
    ```

  - Никогда не используйте аргумент функции `arguments`, он будет более приоритетным над объектом `arguments`, который доступен без объявления для каждой функции.

    ```javascript
    // плохо
    function nope(name, options, arguments) {
      // ...код...
    }

    // хорошо
    function yup(name, options, args) {
      // ...код...
    }
    ```

    **[[⬆]](#Оглавление)**



## <a name='properties'>Свойства</a>

  - Используйте точечную нотацию для доступа к свойствам и методам.

    ```javascript
    var luke = {
      jedi: true,
      age: 28
    };

    // плохо
    var isJedi = luke['jedi'];

    // хорошо
    var isJedi = luke.jedi;
    ```

  - Используйте нотацию с `[]`, когда вы получаете свойство, имя для которого хранится в переменной.

    ```javascript
    var luke = {
      jedi: true,
      age: 28
    };

    function getProp(prop) {
      return luke[prop];
    }

    var isJedi = getProp('jedi');
    ```

    **[[⬆]](#Оглавление)**


## <a name='variables'>Переменные</a>

  - Всегда используйте `var` для объявления переменных. В противном случае переменная будет объявлена глобальной. Загрязнение глобального пространства имен — всегда плохо.

    ```javascript
    // плохо
    superPower = new SuperPower();

    // хорошо
    var superPower = new SuperPower();
    ```

  - Используйте одно `var` объявление переменных для всех переменных, и объявляйте каждую переменную на новой строке.

    ```javascript
    // плохо
    var items = getItems();
    var goSportsTeam = true;
    var dragonball = 'z';

    // хорошо
    var items = getItems(),
        goSportsTeam = true,
        dragonball = 'z';
    ```

  - Объявляйте переменные, которым не присваивается значение, в конце. Это удобно, когда вам необходимо задать значение одной из этих переменных на базе уже присвоенных значений.

    ```javascript
    // плохо
    var i, len, dragonball,
        items = getItems(),
        goSportsTeam = true;

    // плохо
    var i, items = getItems(),
        dragonball,
        goSportsTeam = true,
        len;

    // хорошо
    var items = getItems(),
        goSportsTeam = true,
        dragonball,
        length,
        i;
    ```

  - Присваивайте переменные в начале области видимости. Это помогает избегать проблем с объявлением переменных и областями видимости.

    ```javascript
    // плохо
    function() {
      test();
      console.log('делаю что-нибудь..');

      //..или не делаю...

      var name = getName();

      if (name === 'test') {
        return false;
      }

      return name;
    }

    // хорошо
    function() {
      var name = getName();

      test();
      console.log('делаю что-то полезное..');

      //..продолжаю приносить пользу людям..

      if (name === 'test') {
        return false;
      }

      return name;
    }

    // плохо
    function() {
      var name = getName();

      if (!arguments.length) {
        return false;
      }

      return true;
    }

    // хорошо
    function() {
      if (!arguments.length) {
        return false;
      }

      var name = getName();

      return true;
    }
    ```

    **[[⬆]](#Оглавление)**


## <a name='hoisting'>Области видимости</a>

  - Объявление переменных ограничивается областью видимости, а присвоение — нет.

    ```javascript
    // Мы знаем, что это не будет работать
    // если нет глобальной переменной notDefined
    function example() {
      console.log(notDefined); // => выбрасывает код с ошибкой ReferenceError
    }

    // Декларирование переменной после ссылки на нее
    // не будет работать из-за ограничения области видимости.
    function example() {
      console.log(declaredButNotAssigned); // => undefined
      var declaredButNotAssigned = true;
    }

    // Интерпретатор переносит объявление переменной
    // к верху области видимости.
    // Что значит, что предыдущий пример в действительности
    // будет воспринят интерпретатором так:
    function example() {
      var declaredButNotAssigned;
      console.log(declaredButNotAssigned); // => undefined
      declaredButNotAssigned = true;
    }
    ```

  - Объявление анонимной функции поднимает наверх области видимости саму переменную, но не ее значение.

    ```javascript
    function example() {
      console.log(anonymous); // => undefined

      anonymous(); // => TypeError anonymous is not a function
      // Ошибка типов: переменная anonymous не является функцией и не может быть вызвана

      var anonymous = function() {
        console.log('анонимная функция');
      };
    }
    ```

  - Именованные функции поднимают наверх области видимости переменную, не ее значение. Имя функции при этом недоступно в области видимости переменной и доступно только изнутри.

    ```javascript
    function example() {
      console.log(named); // => undefined

      named(); // => TypeError named is not a function
      // Ошибка типов: переменная named не является функцией и не может быть вызвана

      superPower(); // => ReferenceError superPower is not defined (Ошибка ссылки: переменная superPower не найдена в этой области видимости)

      var named = function superPower() {
        console.log('Я лечууууу');
      };
    }

    // То же самое происходит, когда имя функции и имя переменной совпадают.
    // var named доступно изнутри области видимости функции example.
    // function named доступна только изнутри ее самой.
    function example() {
      console.log(named); // => undefined

      named(); // => TypeError named is not a function
      // Ошибка типов: переменная named не является функцией и не может быть вызвана

      var named = function named() {
        console.log('именованная функция');
      }
    }
    ```

  - Объявления функции поднимают на верх текущей области видимости и имя, и свое значение.

    ```javascript
    function example() {
      superPower(); // => Я лечууууу

      function superPower() {
        console.log('Я лечууууу');
      }
    }
    ```

  - Более подробно можно прочитать в статье [JavaScript Scoping & Hoisting](http://www.adequatelygood.com/2010/2/JavaScript-Scoping-and-Hoisting) от [Ben Cherry](http://www.adequatelygood.com/)

    **[[⬆]](#Оглавление)**



## <a name='conditionals'>Условные выражения и равенства</a>

  - Используйте `===` и `!==` вместо `==` и `!=`.
  - Условные выражения вычисляются посредством приведения к логическому типу Boolean через метод `ToBoolean` и всегда следуют следующим правилам:

    + **Object** всегда соответствует **true**
    + **Undefined** всегда соответствует **false**
    + **Null** всегда соответствует **false**
    + **Boolean** остается неизменным
    + **Number** соответствует **false**, если является **+0, -0, или NaN**, в противном случае соответствует **true**
    + **String** означает **false**, если является пустой строкой `''`, в противном случае **true**. Условно говоря, для строки происходит сравнение не ее самой, а ее длины – в соответствии с типом number.

    ```javascript
    if ([0]) {
      // true
      // Массив(Array) является объектом, объекты преобразуются в true
    }
    ```

  - Используйте короткий синтаксис.

    ```javascript
    // плохо
    if (name !== '') {
      // ...код...
    }

    // хорошо
    if (name) {
      // ...код...
    }

    // плохо
    if (collection.length > 0) {
      // ...код...
    }

    // хорошо
    if (collection.length) {
      // ...код...
    }
    ```

  - Более подробно можно прочитать в статье [Truth Equality and JavaScript](http://javascriptweblog.wordpress.com/2011/02/07/truth-equality-and-javascript/#more-2108) от Angus Croll

    **[[⬆]](#Оглавление)**


## <a name='blocks'>Блоки кода</a>

  - Используйте фигурные скобки для всех многострочных блоков.

    ```javascript
    // плохо
    if (test)
      return false;

    // хорошо
    if (test) return false;

    // хорошо
    if (test) {
      return false;
    }

    // плохо
    function() { return false; }

    // хорошо
    function() {
      return false;
    }
    ```

    **[[⬆]](#Оглавление)**


## <a name='comments'>Комментарии</a>

  - Используйте `/** ... */` для многострочных комментариев. Включите описание, опишите типы и значения для всех параметров и возвращаемых значений в формате jsdoc.

    ```javascript
    // плохо
    // make() возвращает новый элемент
    // основываясь на получаемом имени тэга
    //
    // @param <String> tag
    // @return <Element> element
    function make(tag) {

      // ...создаем element...

      return element;
    }

    // хорошо
    /**
     * make() возвращает новый элемент
     * основываясь на получаемом имени тэга
     *
     * @param <String> tag
     * @return <Element> element
     */
    function make(tag) {

      // ...создаем element...

      return element;
    }
    ```

  - Используйте `//` для комментариев в одну строку. Размещайте комментарии на новой строке над темой комментария. Добавляйте пустую строку над комментарием.

    ```javascript
    // плохо
    var active = true;  // устанавливаем активным элементом

    // хорошо
    // устанавливаем активным элементом
    var active = true;

    // плохо
    function getType() {
      console.log('проверяем тип...');
      // задаем тип по умолчанию 'no type'
      var type = this._type || 'no type';

      return type;
    }

    // хорошо
    function getType() {
      console.log('проверяем тип...');

      // задаем тип по умолчанию 'no type'
      var type = this._type || 'no type';

      return type;
    }
    ```

  - Префикс `TODO` помогает другим разработчикам быстро понять, что вы указываете на проблему, к которой нужно вернуться в дальнейшем, или если вы предлагете решение проблемы, которое должно быть реализовано. Эти комментарии отличаются от обычных комментариев, так как не описывают текущее поведение, а призывают к действию, например `TODO -- нужно реализовать интерфейс`. Такие комментарии также автоматически обнаруживаются многими IDE и редакторами кода, что позволяет быстро перемещаться между ними.

  - Используйте `// TODO FIXME:` для аннотирования проблем

    ```javascript
    function Calculator() {

      // TODO FIXME: тут не нужно использовать глобальную переменную
      total = 0;

      return this;
    }
    ```

  - Используйте `// TODO:` для указания решений проблем

    ```javascript
    function Calculator() {

      // TODO: должна быть возможность изменять значение через параметр функции
      this.total = 0;

      return this;
    }
  ```

    **[[⬆]](#Оглавление)**


## <a name='whitespace'>Пробелы</a>

  - Используйте программную табуляцию (ее поддерживают все современные редакторы кода и IDE) из двух пробелов.

    ```javascript
    // плохо
    function() {
    ∙∙∙∙var name;
    }

    // плохо
    function() {
    ∙var name;
    }

    // хорошо
    function() {
    ∙∙var name;
    }
    ```
  - Устанавливайте один пробел перед открывающей скобкой.

    ```javascript
    // плохо
    function test(){
      console.log('test');
    }

    // хорошо
    function test() {
      console.log('test');
    }

    // плохо
    dog.set('attr',{
      age: '1 year',
      breed: 'Bernese Mountain Dog'
    });

    // хорошо
    dog.set('attr', {
      age: '1 year',
      breed: 'Bernese Mountain Dog'
    });
    ```
  - Оставляйте новую строку в конце файла.

    ```javascript
    // плохо
    (function(global) {
      // ...код...
    })(this);
    ```

    ```javascript
    // хорошо
    (function(global) {
      // ...код...
    })(this);

    ```

  - Используйте отступы, когда делаете цепочки вызовов.

    ```javascript
    // плохо
    $('#items').find('.selected').highlight().end().find('.open').updateCount();

    // хорошо
    $('#items')
      .find('.selected')
        .highlight()
        .end()
      .find('.open')
        .updateCount();

    // плохо
    var leds = stage.selectAll('.led').data(data).enter().append('svg:svg').class('led', true)
        .attr('width',  (radius + margin) * 2).append('svg:g')
        .attr('transform', 'translate(' + (radius + margin) + ',' + (radius + margin) + ')')
        .call(tron.led);

    // хорошо
    var leds = stage.selectAll('.led')
        .data(data)
      .enter().append('svg:svg')
        .class('led', true)
        .attr('width',  (radius + margin) * 2)
      .append('svg:g')
        .attr('transform', 'translate(' + (radius + margin) + ',' + (radius + margin) + ')')
        .call(tron.led);
    ```

    **[[⬆]](#Оглавление)**

## <a name='commas'>Запятые</a>

  - Запятые в начале строки: **Нет.**

    ```javascript
    // плохо
    var once
      , upon
      , aTime;

    // хорошо
    var once,
        upon,
        aTime;

    // плохо
    var hero = {
        firstName: 'Bob'
      , lastName: 'Parr'
      , heroName: 'Mr. Incredible'
      , superPower: 'strength'
    };

    // хорошо
    var hero = {
      firstName: 'Bob',
      lastName: 'Parr',
      heroName: 'Mr. Incredible',
      superPower: 'strength'
    };
    ```

  - Дополнительная запятая в конце объектов: **Нет**. Она способна вызвать проблемы с IE6/7 и IE9 в режиме совместимости. В некоторых реализациях ES3 запятая в конце массива увеличивает его длину на 1, что может вызвать проблемы. Этот вопрос был прояснен только в ES5 ([оригинал](http://es5.github.io/#D)):

  > Редакция ECMAScript 5 однозначно устанавливает факт, что запятая в конце ArrayInitialiser не должна увеличивать длину массива. Это несемантическое изменение от Редакции ECMAScript 3, но некоторые реализации до этого некорректно разрешали этот вопрос.

    ```javascript
    // плохо
    var hero = {
      firstName: 'Kevin',
      lastName: 'Flynn',
    };

    var heroes = [
      'Batman',
      'Superman',
    ];

    // хорошо
    var hero = {
      firstName: 'Kevin',
      lastName: 'Flynn'
    };

    var heroes = [
      'Batman',
      'Superman'
    ];
    ```

    **[[⬆]](#Оглавление)**


## <a name='semicolons'>Точки с запятой</a>

  - **Да.**

    ```javascript
    // плохо
    (function() {
      var name = 'Skywalker'
      return name
    })()

    // хорошо
    (function() {
      var name = 'Skywalker';
      return name;
    })();

    // хорошо
    ;(function() {
      var name = 'Skywalker';
      return name;
    })();
    ```

    **[[⬆]](#Оглавление)**


## <a name='type-coercion'>Приведение типов</a>

  - Выполняйте приведение типов в начале операции, но не делайте его избыточным.
  - Строки:

    ```javascript
    //  => this.reviewScore = 9;

    // плохо
    var totalScore = this.reviewScore + '';

    // хорошо
    var totalScore = '' + this.reviewScore;

    // плохо
    var totalScore = '' + this.reviewScore + ' итого';

    // хорошо
    var totalScore = this.reviewScore + ' итого';
    ```

  - Используйте `parseInt` для чисел и всегда указывайте основание для приведения типов.

    ```javascript
    var inputValue = '4';

    // плохо
    var val = new Number(inputValue);

    // плохо
    var val = +inputValue;

    // плохо
    var val = inputValue >> 0;

    // плохо
    var val = parseInt(inputValue);

    // хорошо
    var val = Number(inputValue);

    // хорошо
    var val = parseInt(inputValue, 10);
    ```

  - Если по какой-либо причине вы делаете что-то дикое, и именно на `parseInt` тратится больше всего ресурсов, используйте побитовый сдвиг [из соображений быстродействия](http://jsperf.com/coercion-vs-casting/3), но обязательно оставьте комментарий с объяснением причин.

    ```javascript
    // хорошо
    /**
     * этот код медленно работал из-за parseInt
     * побитовый сдвиг строки для приведения ее к числу
     * работает значительно быстрее.
     */
    var val = inputValue >> 0;
    ```

  - **Примечание:** Будьте осторожны с побитовыми операциями. Числа в JavaScript являются [64-битными значениями](http://es5.github.io/#x4.3.19), но побитовые операции всегда возвращают 32-битные значенения. [Источник](http://es5.github.io/#x11.7). Побитовые операции над числами, значение которых выходит за 32 бита (верхний предел: 2,147,483,647).

    ```
    2147483647 >> 0 //=> 2147483647
    2147483648 >> 0 //=> -2147483648
    2147483649 >> 0 //=> -2147483647
    ```

  - логические типы(Boolean):

    ```javascript
    var age = 0;

    // плохо
    var hasAge = new Boolean(age);

    // хорошо
    var hasAge = Boolean(age);

    // хорошо
    var hasAge = !!age;
    ```

    **[[⬆]](#Оглавление)**


## <a name='naming-conventions'>Соглашение об именовании</a>

  - Избегайте однобуквенных имен функций. Имена должны давать представление о том, что делает эта функция.

    ```javascript
    // плохо
    function q() {
      // ...код...
    }

    // хорошо
    function query() {
      // ...код...
    }
    ```

  - Используйте camelCase для именования объектов, функций и переменных.

    ```javascript
    // плохо
    var OBJEcttsssss = {};
    var this_is_my_object = {};
    function c() {};
    var u = new user({
      name: 'Bob Parr'
    });

    // хорошо
    var thisIsMyObject = {};
    function thisIsMyFunction() {};
    var user = new User({
      name: 'Bob Parr'
    });
    ```

  - Используйте PascalCase для именования конструкторов классов

    ```javascript
    // плохо
    function user(options) {
      this.name = options.name;
    }

    var bad = new user({
      name: 'Плохиш'
    });

    // хорошо
    function User(options) {
      this.name = options.name;
    }

    var good = new User({
      name: 'Кибальчиш'
    });
    ```

  - Используйте подчеркивание `_` в качестве префикса для именования внутренних методов и переменных объекта.

    ```javascript
    // плохо
    this.__firstName__ = 'Panda';
    this.firstName_ = 'Panda';

    // хорошо
    this._firstName = 'Panda';
    ```

  - Создавая ссылку на `this`, используйте `_this`.

    ```javascript
    // плохо
    function() {
      var self = this;
      return function() {
        console.log(self);
      };
    }

    // плохо
    function() {
      var that = this;
      return function() {
        console.log(that);
      };
    }

    // хорошо
    function() {
      var _this = this;
      return function() {
        console.log(_this);
      };
    }
    ```

  - Задавайте имена для функций. Это повышает читаемость сообщений об ошибках кода.

    ```javascript
    // плохо
    var log = function(msg) {
      console.log(msg);
    };

    // хорошо
    var log = function log(msg) {
      console.log(msg);
    };
    ```

    **[[⬆]](#Оглавление)**


## <a name='accessors'>Геттеры и сеттеры: функции для доступа к значениям объекта</a>

  - Функции универсального доступа к свойствам не требуются
  - Если вам необходимо создать функцию для доступа к переменной, используйте раздельные функции getVal() и setVal('hello')

    ```javascript
    // плохо
    dragon.age();

    // хорошо
    dragon.getAge();

    // плохо
    dragon.age(25);

    // хорошо
    dragon.setAge(25);
    ```

  - Если свойство является логическим(boolean), используйте isVal() или hasVal()

    ```javascript
    // плохо
    if (!dragon.age()) {
      return false;
    }

    // хорошо
    if (!dragon.hasAge()) {
      return false;
    }
    ```

  - Вы можете создавать функции get() и set(), но будьте логичны и последовательны – то есть не добавляйте свойства, которые не могут быть изменены через эти функции.

    ```javascript
    function Jedi(options) {
      options || (options = {});
      var lightsaber = options.lightsaber || 'blue';
      this.set('lightsaber', lightsaber);
    }

    Jedi.prototype.set = function(key, val) {
      this[key] = val;
    };

    Jedi.prototype.get = function(key) {
      return this[key];
    };
    ```

    **[[⬆]](#Оглавление)**


## <a name='constructors'>Конструкторы</a>

  - Присваивайте метод прототипу вместо замены прототипа на другой объект. Замена прототипа на другой объект делает наследование невозможным.

    ```javascript
    function Jedi() {
      console.log('new jedi');
    }

    // плохо
    Jedi.prototype = {
      fight: function fight() {
        console.log('fighting');
      },

      block: function block() {
        console.log('blocking');
      }
    };

    // хорошо
    Jedi.prototype.fight = function fight() {
      console.log('fighting');
    };

    Jedi.prototype.block = function block() {
      console.log('blocking');
    };
    ```

  - Методы могут возвращать `this` для создания цепочек вызовов. Но стоит оставаться последовательным и обеспечить одинаковое поведение для всех методов, кроме геттеров.

    ```javascript
    // плохо
    Jedi.prototype.jump = function() {
      this.jumping = true;
      return true;
    };

    Jedi.prototype.setHeight = function(height) {
      this.height = height;
    };

    var luke = new Jedi();
    luke.jump(); // => true
    luke.setHeight(20) // => undefined

    // хорошо
    Jedi.prototype.jump = function() {
      this.jumping = true;
      return this;
    };

    Jedi.prototype.setHeight = function(height) {
      this.height = height;
      return this;
    };

    var luke = new Jedi();

    luke.jump()
      .setHeight(20);
    ```


  - Вы можете заменить стандартный метод toString(), но убедитесь, что он работает и не вызывает побочных эффектов.

    ```javascript
    function Jedi(options) {
      options || (options = {});
      this.name = options.name || 'no name';
    }

    Jedi.prototype.getName = function getName() {
      return this.name;
    };

    Jedi.prototype.toString = function toString() {
      return 'Jedi - ' + this.getName();
    };
    ```

    **[[⬆]](#Оглавление)**


## <a name='events'>События</a>

  - Подключая набор данных к событиям (как DOM-событиям, так и js-событиям, например, в Backbone), передавайте объект вместо простой переменной. Это позволяет в процессе всплытия событий добавлять к данному объекту дополнительную информацию.

    ```js
    // плохо
    $(this).trigger('listingUpdated', listing.id);

    ...

    $(this).on('listingUpdated', function(e, listing) {
         //делаем что-нибудь с listing, например:
         listing.name = listings[listing.id]
    });
    ```

    prefer:

    ```js
    // хорошо
    $(this).trigger('listingUpdated', { listingId : listing.id });

    ...

    $(this).on('listingUpdated', function(e, data) {
      // делаем что-нибудь с data.listingId
    });
    ```

  **[[⬆]](#Оглавление)**


## <a name='modules'>Модули</a>

  - Модуль должен начинаться с `!`. За счет этого даже некорректно сформированный модуль, в конце которого отсутствует точка с запятой, не вызовет ошибок при автоматической сборке скриптов. [Объяснение](https://github.com/airbnb/javascript/issues/44#issuecomment-13063933)
  - Файл должен быть именован с camelCase, находиться в папке с тем же именем, и совпадать с именем экспортируемой переменной.
  - Добавьте метод noConflict(), устанавливающий экспортируемый модуль в состояние предыдущей версии.
  - Всегда объявляйте `'use strict';` в начале модуля.

    ```javascript
    // fancyInput/fancyInput.js

    !function(global) {
      'use strict';

      var previousFancyInput = global.FancyInput;

      function FancyInput(options) {
        this.options = options || {};
      }

      FancyInput.noConflict = function noConflict() {
        global.FancyInput = previousFancyInput;
        return FancyInput;
      };

      global.FancyInput = FancyInput;
    }(this);
    ```

    **[[⬆]](#Оглавление)**


## <a name='jquery'>jQuery</a>

  - Для jQuery-переменных используйте префикс `$`.

    ```javascript
    // плохо
    var sidebar = $('.sidebar');

    // хорошо
    var $sidebar = $('.sidebar');
    ```

  - Кэшируйте jQuery-запросы. Каждый новый jQuery-запрос делает повторный поиск по DOM-дереву, и приложение начинает работать медленнее.

    ```javascript
    // плохо
    function setSidebar() {
      $('.sidebar').hide();

      // ...код...

      $('.sidebar').css({
        'background-color': 'pink'
      });
    }

    // хорошо
    function setSidebar() {
      var $sidebar = $('.sidebar');
      $sidebar.hide();

      // ...код...

      $sidebar.css({
        'background-color': 'pink'
      });
    }
    ```

  - Для DOM-запросов используйте классический каскадный CSS-синтаксис `$('.sidebar ul')` или родитель > потомок `$('.sidebar > ul')`. [jsPerf](http://jsperf.com/jquery-find-vs-context-sel/16)
  - Используйте `find` для поиска внутри DOM-объекта.

    ```javascript
    // плохо
    $('ul', '.sidebar').hide();

    // плохо
    $('.sidebar').find('ul').hide();

    // хорошо
    $('.sidebar ul').hide();

    // хорошо
    $('.sidebar > ul').hide();

    // хорошо
    $sidebar.find('ul');
    ```

    **[[⬆]](#Оглавление)**


## <a name='es5'>Совместимость ECMAScript 5</a>

  - Опирайтесь на [таблицу совместимости](http://kangax.github.com/es5-compat-table/) с ES5 от [Kangax](https://twitter.com/kangax/)

  **[[⬆]](#Оглавление)**


## <a name='testing'>Тестирование</a>

  - **Да.**

    ```javascript
    function() {
      return true;
    }
    ```

    **[[⬆]](#Оглавление)**


## <a name='performance'>Быстродействие</a>

  - [On Layout & Web Performance](http://kellegous.com/j/2013/01/26/layout-performance/)
  - [String vs Array Concat](http://jsperf.com/string-vs-array-concat/2)
  - [Try/Catch Cost In a Loop](http://jsperf.com/try-catch-in-loop-cost)
  - [Bang Function](http://jsperf.com/bang-function)
  - [jQuery Find vs Context, Selector](http://jsperf.com/jquery-find-vs-context-sel/13)
  - [innerHTML vs textContent for script text](http://jsperf.com/innerhtml-vs-textcontent-for-script-text)
  - [Long String Concatenation](http://jsperf.com/ya-string-concat)
  - В процессе наполнения...

  **[[⬆]](#Оглавление)**


## <a name='resources'>Ресурсы</a>


**Прочитайте это**

  - [Annotated ECMAScript 5.1](http://es5.github.com/)

**Другие руководства по стилю**

  - [Google JavaScript Style Guide](http://google-styleguide.googlecode.com/svn/trunk/javascriptguide.xml)
  - [jQuery Core Style Guidelines](http://docs.jquery.com/JQuery_Core_Style_Guidelines)
  - [Principles of Writing Consistent, Idiomatic JavaScript](https://github.com/rwldrn/idiomatic.js/)

**Другие стили**

  - [Naming this in nested functions](https://gist.github.com/4135065) - Christian Johansen
  - [Conditional Callbacks](https://github.com/airbnb/javascript/issues/52)
  - [Popular JavaScript Coding Conventions on Github](http://sideeffect.kr/popularconvention/#javascript)

**Дальнейшее прочтение**

  - [Understanding JavaScript Closures](http://javascriptweblog.wordpress.com/2010/10/25/understanding-javascript-closures/) - Angus Croll
  - [Basic JavaScript for the impatient programmer](http://www.2ality.com/2013/06/basic-javascript.html) - Dr. Axel Rauschmayer

**Книги**

  - [JavaScript: The Good Parts](http://www.amazon.com/JavaScript-Good-Parts-Douglas-Crockford/dp/0596517742) - Douglas Crockford
  - [JavaScript Patterns](http://www.amazon.com/JavaScript-Patterns-Stoyan-Stefanov/dp/0596806752) - Stoyan Stefanov
  - [Pro JavaScript Design Patterns](http://www.amazon.com/JavaScript-Design-Patterns-Recipes-Problem-Solution/dp/159059908X)  - Ross Harmes and Dustin Diaz
  - [High Performance Web Sites: Essential Knowledge for Front-End Engineers](http://www.amazon.com/High-Performance-Web-Sites-Essential/dp/0596529309) - Steve Souders
  - [Maintainable JavaScript](http://www.amazon.com/Maintainable-JavaScript-Nicholas-C-Zakas/dp/1449327680) - Nicholas C. Zakas
  - [JavaScript Web Applications](http://www.amazon.com/JavaScript-Web-Applications-Alex-MacCaw/dp/144930351X) - Alex MacCaw
  - [Pro JavaScript Techniques](http://www.amazon.com/Pro-JavaScript-Techniques-John-Resig/dp/1590597273) - John Resig
  - [Smashing Node.js: JavaScript Everywhere](http://www.amazon.com/Smashing-Node-js-JavaScript-Everywhere-Magazine/dp/1119962595) - Guillermo Rauch
  - [Secrets of the JavaScript Ninja](http://www.amazon.com/Secrets-JavaScript-Ninja-John-Resig/dp/193398869X) - John Resig and Bear Bibeault
  - [Human JavaScript](http://humanjavascript.com/) - Henrik Joreteg
  - [Superhero.js](http://superherojs.com/) - Kim Joar Bekkelund, Mads Mobæk, & Olav Bjorkoy
  - [JSBooks](http://jsbooks.revolunet.com/)

**Блоги**

  - [DailyJS](http://dailyjs.com/)
  - [JavaScript Weekly](http://javascriptweekly.com/)
  - [JavaScript, JavaScript...](http://javascriptweblog.wordpress.com/)
  - [Bocoup Weblog](http://weblog.bocoup.com/)
  - [Adequately Good](http://www.adequatelygood.com/)
  - [NCZOnline](http://www.nczonline.net/)
  - [Perfection Kills](http://perfectionkills.com/)
  - [Ben Alman](http://benalman.com/)
  - [Dmitry Baranovskiy](http://dmitry.baranovskiy.com/)
  - [Dustin Diaz](http://dustindiaz.com/)
  - [nettuts](http://net.tutsplus.com/?s=javascript)

  **[[⬆]](#Оглавление)**

## <a name='in-the-wild'>В реальном мире</a>

  Вот неполный список организаций, которые опираются на оригинальное руководство от AirBnB. Если вы собираетесь использовать это переведенное руководство, сделайте pull request, и мы сможем начать отдельный список компаний, использующих данный перевод.

  - **Aan Zee**: [AanZee/javascript](https://github.com/AanZee/javascript)
  - **Airbnb**: [airbnb/javascript](https://github.com/airbnb/javascript)
  - **American Insitutes for Research**: [AIRAST/javascript](https://github.com/AIRAST/javascript)
  - **Compass Learning**: [compasslearning/javascript-style-guide](https://github.com/compasslearning/javascript-style-guide)
  - **ExactTarget**: [ExactTarget/javascript](https://github.com/ExactTarget/javascript)
  - **Gawker Media**: [gawkermedia/javascript](https://github.com/gawkermedia/javascript)
  - **GeneralElectric**: [GeneralElectric/javascript](https://github.com/GeneralElectric/javascript)
  - **GoodData**: [gooddata/gdc-js-style](https://github.com/gooddata/gdc-js-style)
  - **Grooveshark**: [grooveshark/javascript](https://github.com/grooveshark/javascript)
  - **How About We**: [howaboutwe/javascript](https://github.com/howaboutwe/javascript)
  - **Mighty Spring**: [mightyspring/javascript](https://github.com/mightyspring/javascript)
  - **MinnPost**: [MinnPost/javascript](https://github.com/MinnPost/javascript)
  - **ModCloth**: [modcloth/javascript](https://github.com/modcloth/javascript)
  - **National Geographic**: [natgeo/javascript](https://github.com/natgeo/javascript)
  - **National Park Service**: [nationalparkservice/javascript](https://github.com/nationalparkservice/javascript)
  - **Razorfish**: [razorfish/javascript-style-guide](https://github.com/razorfish/javascript-style-guide)
  - **Shutterfly**: [shutterfly/javascript](https://github.com/shutterfly/javascript)
  - **Userify**: [userify/javascript](https://github.com/userify/javascript)
  - **Zillow**: [zillow/javascript](https://github.com/zillow/javascript)
  - **ZocDoc**: [ZocDoc/javascript](https://github.com/ZocDoc/javascript)

## <a name='translation'>Переводы</a>

  Это руководство так же переведено на:

  - :de: **Немецкий**: [timofurrer/javascript-style-guide](https://github.com/timofurrer/javascript-style-guide)
  - :jp: **Японский**: [mitsuruog/javacript-style-guide](https://github.com/mitsuruog/javacript-style-guide)
  - :br: **Португальский**: [armoucar/javascript-style-guide](https://github.com/armoucar/javascript-style-guide)
  - :cn: **Китайский**: [adamlu/javascript-style-guide](https://github.com/adamlu/javascript-style-guide)
  - :es: **Испанский**: [paolocarrasco/javascript-style-guide](https://github.com/paolocarrasco/javascript-style-guide)
  - :kr: **Корейский**: [tipjs/javascript-style-guide](https://github.com/tipjs/javascript-style-guide)

## <a name='license'>Лицензия</a>

(The MIT License)

Copyright (c) 2012 Airbnb: оригинальный текст, (c) 2013 Uprock: перевод

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
'Software'), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

**[[⬆]](#Оглавление)**

