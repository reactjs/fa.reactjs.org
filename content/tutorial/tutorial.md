---
id: tutorial
title: "مقدمه‌ای بر ری‌اکت"
layout: tutorial
sectionid: tutorial
permalink: tutorial/tutorial.html
redirect_from:
  - "docs/tutorial.html"
  - "docs/why-react.html"
  - "docs/tutorial-ja-JP.html"
  - "docs/tutorial-ko-KR.html"
  - "docs/tutorial-zh-CN.html"
---

### برای افراد مشتاق به یادگیری
در این آموزش فرض بر این گذاشته شده که شما هیچ شناخت و تجربه‌ای در ری‌اکت ندارید.

## قبل از اینکه آموزش را شروع کنیم {#before-we-start-the-tutorial}

لازم به ذکر است که در طول این آموزش ما بازی کوچکی می‌سازیم و از شما خواهشمندیم حتا اگر قصد بازی سازی ندارید از آن سرپوشی نکنید. زیرا که تکنیک‌های مورد استفاده در این آموزش و این بازی، پایه و اساس برنامه‌نویسی با ری‌اکت است و تبحر در آن می‌تواند موجب درک عمیق ری‌اکت در شما شود.

>نکته
> 
>این آموزش برای افرادی طراحی شده ترجیح می‌دهند به صورت پروژه محور و با حل مثال‌ها، مباحث را بیاموزند. در صورتی که تمایل دارید مسائل را از پایه بیاموزید به [راهنمای قدم به قدم ری‌اکت](https://reactjs.org/docs/hello-world.html) رجوع کنید. شاید این آموزش و راهنمای گام‌به‌گام برای شما مکمل هم‌دیگر باشند.  


سرفصل مباحث به این صورت است:

* [آماده‌سازی](#setup-for-the-tutorial): آماده‌سازی سیستم و نصب ابزارهای مورد نیاز
* [بررسی اجمالی](#overview): یادگیری مفاهیم مثل کامپوننت‌ها، props و state
* [کامل کردن بازی](#completing-the-game): یادگیری تکنیک‌های مهم برنامه‌نویسی ری‌اکت
* [اضافه کردن دکمه‌ی برگشت](#adding-time-travel): یک دید عمیق‌تر به توانایی‌های منحصر به فرد ری‌اکت.

برای یادگیری مفاهیم موجود در این آموزش بهتر است به جای تکمیل همزمان بخش‌ها، آن‌ها را به مرور تمرین و تکرار کنید.

### چه خواهیم ساخت؟ {#what-are-we-building}

یک بازی tic-tac-toe یا همان دوز خودمان. کد نهایی بازی را از [اینجا](https://codepen.io/gaearon/pen/gWWZgR?editors=0010) بررسی کنید. اگر چیزی متوجه نشدید و نحوه‌ی نگارش کدها برایتان ناآشنا بود نگران نباشید به زودی آشنا خواهند شد.
شدیدا توصیه می‌شود قبل شروع این آموزش، خود بازی را نگاهی بیندازید. یکی از ویژگی‌هایی که باید به آن توجه کنید لیست عددهایی است که در سمت راست بازی نمایش داده می‌شوند. این‌ها یک تاریخچه از حرکت‌هایی بازی را نشان می‌دهند و در طول بازی تغییر میکند.
حالا اگر با این بازی آشنایی دارید می‌توانید آن را خارج کنید. ما ابتدا از قالب ساده‌تری شروع می‌کنیم و در مرحله‌ی بعد شروع به ساخت بازی خواهیم کرد.

### پبش‌نیاز‌ها {#prerequisites}

 - آشنایی با HTML و JavaScript(اگر برنامه‌نویس زبان دیگری هستید احتمالا قادر خواهید بود با آموزش پیش بیایید)
 - کدهای CSS به صورت آماده فراهم شده‌اند تا تمرکز بر روی یادگیری ری‌اکت گردد. ولی در ساخت صفحات وب، بسیار پیشنهاد می‌شود که به CSS مسلط باشید.
 - آشنایی با مفاهیم برنامه‌نویسی مثل توابع، اشیاء، آرایه‌ها و کلاس‌ها
 - آشنایی با ویژگی‌های ES6 جاوا اسکریپت(نسخه‌ی اخیر آن) مانند [توابع جهت‌دار](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions)، [کلاس‌ها](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes) و دستورهای [let](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let) و [const](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/const). میتوانید از ‌[Babel REPL](babel://es5-syntax-example) برای چک اینکه کدهای ES6 در نهایت به چه کدی تبدیل می‌شوند، استفاده کنید.

## آماده‌سازی  {#setup-for-the-tutorial}

برای اجرای کدهای ری‌اکت و پیش رفتن با این آموزش از دو روش می‌تونیم اقدام کنید.

### روش ۱: نوشتن و اجرای کدها در مرورگر {#setup-option-1-write-code-in-the-browser}
سریع‌ترین روش است. ابتدا کد اولیه را در تب جدید مرورگر باز کنید. یک بازی(ناقص) و در سمت دیگر کدهای ری‌اکت را خواهید دید. حالا می‌توانید با ادیت کردن کدها به این آموزش ادامه دهید و اکنون به بخش [نمای کلی](#overview) بروید.

### روش ۲: راه‌اندازی محیط محلی یا لوکال ری‌اکت {#setup-option-2-local-development-environment}

کاملا اختیاری و برای این آموزش الزامی نیست.

<br>

<details>

<summary><b>: راه‌اندازی محیط محلی</b></summary>

این روش نیازمند صرف توان و زمان بیش‌تری است اما در عوض به شما اجازه می‌دهد با ادیتور دلخواهتان کدها را ویرایش کنید. علاوه بر آن زمانی که تصمیم دارید بر روی سرور خودتان کار کنید روش اول نمی‌تواند پاسخگوی نیازتان باشد.

1.  ابتدا اطمینان حاصل کنید که [Node.js](https://nodejs.org/fa/) را بر روی سیستم نصب دارید.

2.   [راهنمای ایجاد یک پروژه‌ی ری‌اکت](/docs/create-a-new-react-app.html#create-react-app) را دنبال کنید تا یک پروژه جدید بسازید.
``` bash
npx create-react-app my-app
```
3. تمامی فایل‌های داخل پوشه‌ی `src/` پروژه‌ی ایجاد شده را پاک کنید.
توجه داشته باشید: کل پوشه‌ی src را پاک نکنید، فقط سورس فایل‌های. در مرحله‌ی بعد سورس‌فایل‌‌ پیش‌فرض با فایل‌های مورد نظرمان جایگزین خواهیم کرد.
> نکته:
>
> توجه کنید که خود پوشه‌ی src را به جای محتویاتش پاک نکنید.(اگر کردید دوباره آن را بسازید)

```bash
cd my-app
cd src

# If you're using a Mac or Linux:
rm -f *

# Or, if you're on Windows:

del *

# Then, switch back to the project folder

cd ..
```


4. در پوشه‌ی src یک فایل با نام index.css و با [این محتویات](https://codepen.io/gaearon/pen/oWWQNa?editors=0100) ایجاد کنید.

5. در پوشه‌ی src یک فایل دیگر به نام index.js با [این محتویات](https://codepen.io/gaearon/pen/oWWQNa?editors=0010) ایجاد کنید.
    و این سه خط را به بالای index.js اضافه کنید.

  ```js
import React from 'react';
import ReactDOM from 'react-dom';
import './index.css';
  ```

حالا اگر npm start را در پوشه‌ی پروژه اجرا و در مرورگر `http://localhost:3000` را باز کنید، یک بازی tic-tac-toe خالی خواهید دید.

اگر تمایل دارید رنگ بندی کدها یا syntax highlighting ادیتور خودتون رو تنظیم کنید، میتوانید این [دستورالعمل‌ها](https://babeljs.io/docs/editors/) را دنبال کنید.
</details>

### ارتباط با ما {#help-im-stuck}

اگر در طول این دوره جایی به مشکل برخوردید به [این جا](https://reactjs.org/community/support.html) رجوع کنید. در مواقع خاص [Reactiflux Chat](https://discord.gg/reactiflux) هم می‌تواند روشی سریع برای کمک گرفتن باشد. اما اگر نیاز به کمک به زمان فارسی دارید، می‌توانید به انجمن [جامعه ری‌اکت ایران](https://iran-react-community.github.io/) سر زده و سوال خود را در آنجا بپرسید. 

این آموزش متن‌باز و بر روی گیت‌هاب هاست شده، پس در صورت هرگونه اشتباه، غلط املایی، ناقص بودن مطالب و ... آن را از [اینجا](https://github.com/reactjs/fa.reactjs.org/issues/new) با ما در میان بگذارید و در صورت تمایل به حمایت، آن‌ها را حل کرده و به [گیت‌هاب این سایت](https://github.com/reactjs/fa.reactjs.org) pull request بزنید.

## نمای کلی {#overview}

حالا که ابزارهای مورد نیاز نصب شده و آماده‌اید بیایید یک دید کلی از ری‌اکت به دست آوریم.

### ری‌اکت چیست؟ {#what-is-react}

ری‌اکت یک کتابخانه کارآمد و بسیار انعطاف پذیر برای جاوا اسکریپت است که به شما این اجازه را می‌دهد که از تکه‌ها کوچک و ساده، رابط کاربری‌های پیچیده بسازید. این تکه‌های کوچک کامپوننت‌ها(component ها) هستند.


در ری‌اکت چند نوع کامپوننت وجود دارد که با زیر کلاس `React.Component` شروع می‌کنیم:

```javascript
class ShoppingList extends React.Component {
  render() {
    return (
      <div className="shopping-list">
        <h1>Shopping List for {this.props.name}</h1>
        <ul>
          <li>Instagram</li>
          <li>WhatsApp</li>
          <li>Oculus</li>
        </ul>
      </div>
    );
  }
}

// Example usage: <ShoppingList name="Mark" />
```

با استفاده از کامپوننت‌ها، ما به ری‌اکت توضیح می‌دهیم چه چیزی باید روی صفحه نمایان شود. وقتی که کامپوننت یا داده های ما دچار تغییر شد ری‌اکت به صورت اتوماتیک تنها قسمت تغییر یافته و فرزندانش را دوباره رندر و آپدیت می‌کند(البته با استفاده از تکنولوژی Virtual DOM تلاش می‌کند که تنها قیمت‌هایی که دچار تغییر شده‌اند را رندر بگیرد).

در این جا `Shopping List` **از کلاس کامپوننت ری‌اکت** یا در اصل **از نوعی کامپوننت ری‌اکت** است. شما اکنون یک کانپونتت ساخته‌اید و کانپونتت‌های کوچک دیگری(تگ‌هایی XML مانند) در آن قرار داده‌ایم. در ری‌اکت هر کامپوننت میتواند پارامترهایی را هنگام فراخوانی دریافت کند که به آن prop گفته می‌شود(مخفف properties) و لیستی از عضوهایی که باید بر روی صفحه نمایش داده شوند از طریق متد `render` برگشت می‌دهد.

متد `render` **توضیحاتی** مربوط به عناصری که بر روی صفحه خواهیم دید را بر می‌گرداند و سپس ری‌اکت توضیحات را دریافت کرده و نتیجه را بر روی صفحه نمایش می‌دهد. در اصل متد `render` یک **المان ری‌اکت** که توضیح مختصری درباره چیزی که باید رندر شود را در بردارد، بر می‌گرداند. در کد بالا از روش JSX برای مشخص کردن و قرار دادن عناصر استفاده شده است. یعنی به جای ساخت شیٔ با `React.createElement("tagname")` از `</tagname>` استفاده شده است. این کدهای شبه XML در زمان تحلیل به نوع اصلی تبدیل می‌گردند. در برنامه‌نویسی ری‌اکت استفاده از JSX بسیار مرسوم است. برای مثال در متد `render` مثال بالا می‌توان از این کد استفاده کرد:

```javascript
return React.createElement('div', {className: 'shopping-list'},
  React.createElement('h1', /* ... h1 children ... */),
  React.createElement('ul', /* ... ul children ... */)
);
```

[مشاهده‌ی کد کاملا گسترش یافته](babel://tutorial-expanded-version)

اگر کنجکاو هستید `createElement()` در [مرجع API](/docs/react-api.html#createelement) با جزئیات بیشتری توضیح داده شده است ولی در این آموزش از آن استفاده نخواهیم کرد و با JSX ادامه خواهیم داد. در JSX نیز می‌توانید از کدهای جاوا اسکریپت استفاده کنید و تنها لازم است کد مورد نیاز را در پرانتز قرار دهید. و البته به یاد داشته باشید که هر شئ ری‌اکت یک شئ جاوا اسکریپت است که میتواند در یک متغیر ذخیره و یا در کدهای جاوا اسکریپت شما استفاده شود.

در بالا `Shopping list` تنها چند کامپوننت DOM مثل `</ div>` و `</ li>` را نشان می‌دهد اما شما می‌توانید یک کاپوننت سفارشی دیگر ساخته و آن را در نیز در آن قرار دهید. یا می‌توان کامپوننت دیگری ساخته و کل `Shopping list` را با نوشتن `</shopping list>` در آن قرار داد. در ری‌اکت همه کامپونتت‌ها می‌توانند محصور شده و به صورت مستقل کارهای خاصی را انجام دهند. همین ویژگی به شما اجازه می‌دهد از کامپوننت‌های ساده رابط گرافیکی های پیچیده بسازید.

## بررسی کد اولیه {#inspecting-the-starter-code}

اگر ری‌اکت را از طریق مرورگر اجرا می‌کنید، **[Starter Code](https://codepen.io/gaearon/pen/oWWQNa?editors=0010)** را در یک تب جدید باز کنید و در صورتی که ری‌اکت را به صورت محلی نصب کرده‌اید در پوشه‌ی پروژه‌ی خود `src/index.js` را با ویرایش گر دلخواه خود باز کنید.(شما قبلا در طول [راه‌اندازی محیط لوکال](#setup-option-2-local-development-environment) این فایل را ایجاد کرده بودید)

Starter Code(کد اولیه) پایه‌ی اصلی بازی ماست و ما بازی را بر روی آن پیاده‌سازی می‌کنیم.

با کمی نگاه و بررسی کد‌ها متوجه خواهید شد که در آن سه نوع کامپوننت وجود دارد:

* Square
* Board
* Game

کامپوننت Square یک دکمه رندر می‌کند و هر کامپوننت Board، نُه Square را در بر دارد. کامپوننت Game هم دارای یک  Board و چند شئ کوچک است که بعدا آن را خواهیم ساخت فعلا در این کد هیچ کامپوننت فعال و تعاملی‌ای وجود ندارد.

## گذر دادن اطلاعات از طریق Props {#passing-data-through-props}

وقت آن رسیده تا شروع به کامل کردن کد اولیه کنیم. کاری لازم است در ابتدا انجام دهیم آن است که مقداری داده را از کامپوننت Board به Square انتقال دهیم.

شدیدا به شما توصیه می‌کنیم که به جای کپی پیست کردن کدها، آن‌ها را تایپ کنید. این ترفند و شما کمک می‌کند که درک بهتری از ری‌اکت و مفاهیم آن پیدا کرده و ماهیچه‌های حافظه‌تان را نیز تقویت کنید.

اکنون در متد `renderSquare` کد را به صورت زیر تغییر می‌دهیم تا یک prop به نام `value` را به هر Square بفرستیم.

```js{3}
class Board extends React.Component {
  renderSquare(i) {
    return <Square value={i} />;
  }
}
```
حال برای نمایش مقدار value در مربع‌ها ‍‍‍‍`{this.props.value}‍` را جایگزین `{/* TODO /*}` می‌کنیم. در نهایت کلاس Square ما به این صورت خواهد بود:

```js{5}
class Square extends React.Component {
  render() {
    return (
      <button className="square">
        {this.props.value}
      </button>
    );
  }
}
```

قبل از اعمال تغییر:

![before](../images/tutorial/tictac-empty.png)

بعد اعمال: شما باید اعدادی را در هر مربع ببینید.

![after](../images/tutorial/tictac-numbers.png)

**[مشاهده‌ی کد کامل](https://codepen.io/gaearon/pen/aWWQOG?editors=0010)**

تبریک، شما یک prop را از کامپوننت Board به یک Square انتقال دادید. عبور دادن prop از کامپوننت‌ها به ما اجازه می‌دهد اطلاعات را از کامپوننت پدر به پسر انتقال دهیم.

## ساخت یک کامپوننت تعاملی {#making-an-interactive-component}

بیایید کاری کنیم که وقتی روی هر Square کلیک شد، روی آن کلمه‌ی "X" را نمایش داده شود. ابتدا تگ button را که از هر Square برگشت داده می‌شود را تغییر می‌دهیم:

```javascript{4}
class Square extends React.Component {
  render() {
    return (
      <button className="square" onClick={function() { alert('click'); }}>
        {this.props.value}
      </button>
    );
  }
}
```

اکنون اگر روی هر Square کلیک شود،  مرورگر پیام click نمایش داده می‌دهد.

> نکته
>
> در اینجا و از این به بعد برای اینکه در تایپ کردن صرفه‌جویی کرده و [سردگمی هنگام کار با `this` ](https://yehudakatz.com/2011/08/11/understanding-javascript-function-invocation-and-this/) خلاص شویم در کنترل رخدادها و مانند کد پایین از [توابع جهت دار](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions) استفاده می‌کنیم:
>
>```javascript{4}
>class Square extends React.Component {
>  render() {
>    return (
>      <button className="square" onClick={function() { alert('click'); }}>
>        {this.props.value}
>      </button>
>    );
>  }
>}
>```
>
> دقت کنید با استفاده از `onClick={() => alert('click')` **یک تابع** را درون `onClick()` این دکمه قرار داده‌ایم پس ری‌اکت بعد از هر کلیک این تابع را اجرا خواهد کرد. فراموش  `() =>` و نوشتن `onClick{alert('click')` یک اشتباه بسیار رایج است که باعث می‌شود هر زمانی که ری‌اکت صفحه را دوباره رندر می‌کند پیامان نشان داده شود.

به عنوان مرحله‌ی بعدی، می‌خواهیم هر مربعی کلیک می‌شود خود به خاطر بسپارد و عبارت  "X" نمایش بدهد. برای اینکه کامپوننتی چیزی را به خاطر بسپارد از **state** استفاده می‌کنیم.

برای استفاده از state، ابتدا باید `this.state` را در constructor آن به صورت خصوصی(نه گلوبال) تعریف کنیم. حالا باید مقدار داخل مربع‌ها را در `this.state` ذخیره کرده و در زمان کلیک آن را تغییر دهیم.

ابتدا متد constructor را به منظور مقدار دهی اولیه stateها ایجاد می‌کنیم:

```javascript{2-7}
class Square extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      value: null,
    };
  }

  render() {
    return (
      <button className="square" onClick={() => alert('click')}>
        {this.props.value}
      </button>
    );
  }
}
```

>نکته
>
>در [کلاس های جاوا اسکریپت](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes)، باید همیشه در هنگام ساخت constructor یک کلاس که از یک کلاس دیگر منشعب می‌شود(ارث می‌برد)، `super` را صدا بزنیم. پس همه‌ی کامپوننت‌های ری‌اکت که نیازمند به متد `constructor` هستند باید با `super(props)` شروع شوند.

اکنون متد `render` کلاس Square را طوری تغییری ‌می‌دهیم تا زمانی که کلیک شد مقدار متغیر value را نمایش دهد.

* در تگ `<button>` عبارت `this.props.value` را با `this.state.value` جایگزین می‌کنیم.
* عبارت `onClick={...}` را با ` onClick={() => this.setState({value='X'})}` جایگزین می‌کنیم.
* برای خوانایی بیش تر `className` و `onClick` را در خط های جداگانه قرار می‌دهیم.

بعد از این تغییرات باید آن تگ ‍`<button>` که از متد `render` کامپوننت Square برگشت داده می‌شود چیزی شبیه به این باشد:

```javascript{12-13,15}
class Square extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      value: null,
    };
  }

  render() {
    return (
      <button
        className="square"
        onClick={() => this.setState({value: 'X'})}
      >
        {this.state.value}
      </button>
    );
  }
}
```

با صدا زدن `this.setState` از کنترلر `onClick` واقع در متد `render`، به ری‌اکت می‌گوییم هر زمانی که ‍`<button>` کلیک شد، مقدار `this.state.value` برابر `'X'` کرده و Square را دوباره رندر کن. بنابراین کلمه‌ی `X` بر روی صفحه ظاهر می‌شود.
>نکته
>
>وقتی که متد `setState` صدا زده می‌شود، ری‌اکت به صورت اتوماتیک آن کامپوننت و فرزندانش را دوباره رندر می‌کند و آپدیت می‌شوند.

**[مشاهده‌ی کد کامل](https://codepen.io/gaearon/pen/VbbVLg?editors=0010)**

### ابزار برنامه نویسان {#developer-tools}

  افزونه‌ی React Devtools را برای [کروم](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi?hl=en) یا [فایرفاکس](https://addons.mozilla.org/en-US/firefox/addon/react-devtools/) نصب کنید. این افزونه به شما اجازه می‌دهد کامپوننت‌های ری‌اکت را در قسمت developer tools مرورگر خود مشاهده و بازرسی کنید.(در اکثر مرورگرها با فشردن دکمه‌ی F12 وارد قیمت برنامه نویسان خواهید شد.)

<img src="../images/tutorial/devtools.png" alt="React Devtools" style="max-width: 100%">

با استفاده از افزونه React Devtools میتوانید propها و stateهای هر کامپوننت را چک و مورد بررسی قرار دهید. بعد از نصب افزونه با راست کلیک کردن روی صفحه و انتخاب Inspect صفحه‌ی developer tools باز شده و تب‌های ری‌اکت ("⚛️ Components" و  "⚛️ Profiler") در آخرین تب در سمت راست ظاهر می‌شود و شما می‌توانید برای بررسی کامپوننت‌ها از آن استفاده کنید.

**اما برای این که این افزونه با CodePen هم کار کند نیازمند چند کار کوچک هستید.**

1. ثبت نام یا ورود کرده و در صورت ثبت نام ایمیل خود را تایید کنید (این کار به منظور جلوگیری از هرزنامه یا اسپم است).
2. روی دکمه‌ی Fork کلیک کنید.
3. روی Change View کلیک کرده و Debug mode را انتخاب کنید.
4. در تب جدید باز شده، developer tools باید دارای تب مخصوص ری‌اکت باشد.

## کامل کردن بازی {#completing-the-game}

ما الآن بلوک های اساسی بازی مان را در اختیار داریم. چیزی که نیاز داریم این است که روی صفحه‌ی بازی به نوبت "X" و "O" قرار بگیرد و در مرحله‌ی بعد برنده‌ی بازی تعیین شود.

### بالا بردن state (منتقل به کامپوننت‌های بالا‌تر) {#lifting-state-up}

هم اکنون هر Square یک state را برای خودش نگه می‌دارد. برای یافتن برنده ما نیازمندیم مقدارهای همه مربع ها را در یک جا داشته باشیم.
    
شاید تصور کنید Board باید از هر Square مقدار state را بپرسد و در مکانی ذخیره کند. اما با اینکه این حالت در ری‌اکت امکان پذیر است اما پیشنهاد می‌کنیم که از آن استفاده نکنید زیرا که باعث سخت شدن فهم کد، مستعد به افزایش باگ‌ها، سخت شدن بازسازی و بهبود و … می‌شود. در عوض ما می‌توانیم که حالت و موقعیت بازی را به جای هر Square در کامپوننت پدرشان یعنی Board ذخیره کنیم. بنابراین Board با فرستادن یک prop به هر Square به او می‌گوید که  چه چیزی را باید نمایش دهد. شبیه به کاری که برای  [فرستادن یک عدد به مربع‌ها](#passing-data-through-props) انجام داده بودیم.

**برای جمع کردن داده‌ها از چند کامپوننت فرزند یا داشتن دو  کامپوننت که با هم تعامل و ارتباط داشته باشند نیاز به یک state به اشتراک گذاشته شده در تگ پدر داریم. کامپوننت پدر با استفاده از عبور دادن props، داده‌ها را به فرزندان باز می‌گرداند و بین آن‌ها ارتباط برقرار می‌کند. پس دو فرزند با کمک کامپوننت پدر همواره هم‌گام و دارای ارتباط می‌شوند.**

در اینگونه موارد فرستادن state به کامپوننت پدر(بالا بردن state) بسیار رایج است. پس فرصتی به آن بدهید و امتحانش کنید.

تابع constructor را به کلاس Board اضافه کرده و مقدار اولیه state را یک آرایه با ۹ عضو که همگی null(متغیری که خالی است) هستند تعریف کنید.

```javascript{2-7}
class Board extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      squares: Array(9).fill(null),
    };
  }

  renderSquare(i) {
    return <Square value={i} />;
  }
```

در طول بازی، آرایه `this.state.squares` باید چیزی شبیه کد زیر باشد:

```javascript
[
  'O', null, 'X',
  'X', 'X', 'O',
  'O', null, null,
]
```

هم اکنون نیز تابع `renderSquare` کامپوننت Board به این صورت است:

```javascript
  renderSquare(i) {
    return <Square value={i} />;
  }
```

در ابتدا، [پراپس value از طرف Board به هر Square برای نمایش ۰ تا ۸ فرستاده می‌فرستادیم](#passing-data-through-props) اما در مرحله‌ی قبل علاوه براین که X جایگزین عدد کردیم مقدار(چیزی که باید نمایش دهد) هر Square نیز  [بر اساس state خودش](#making-an-interactive-component) قرار دادیم. به همین دلیل است که هم‌اکنون Square پراپ `value` که از طرف Board به آن ارسال می‌شود را نادیده می‌گیرد.

الآن دوباره از مکانیسم فرستادن prop استفاده خواهیم کرد. در کلاس Board باید تغییراتی دهیم تا به هر Square مقدار مخصوصش(`null` یا `'O'` یا `'X'`) را بفرستد. ما قبلا آرایه‌ی squares را در متد constructor بورد تعریف کرده بودیم و الآن تنها باید تغییراتی را در متد `renderSquare` کلاس Board ایجاد کنیم تا بر اساس آن پراپ `value` را به Square بفرستد:

```javascript{2}
  renderSquare(i) {
    return <Square value={this.state.squares[i]} />;
  }
```

**[مشاهده‌ی کد کامل](https://codepen.io/gaearon/pen/gWWQPY?editors=0010)**

هم اکنون هر Square یک پراپس به نام `value` دریافت می‌کند که دارای یکی از مقادیر `'X'` یا `'O'` یا `null` برای مربع‌های خالی است.

در مرحله‌ی بعد نیاز داریم فرآیندی که هنگام کلیک یک مربع اجرا می‌شود را اصلاح کنیم. هم اکنون Board، لیست مقدار مربع‌ها را در خود نگه می‌دارد و کاری که باید انجام دهیم این است که راهی ایجاد کنیم تا در هنگام بازی Square‌ها بتوانند مقدار state بورد را به روز کنند. توجه کنید که state‌ها به صورت خصوصی هستند و از کامپوننت‌های دیگر قابل دسترسی و تغییر نیستند.

اما به جای آن می‌توانیم تابعی را(برای تغییر state مربع‌ها) از Board به Square فرستاده تا Square هر وقت لازم داشت (در این هنگام کلیک) آن را صدا بزند. پس متد `renderSquare` را به کد زیر تغییر می‌دهیم:

```javascript{5}
  renderSquare(i) {
    return (
      <Square
        value={this.state.squares[i]}
        onClick={() => this.handleClick(i)}
        />
    );
  }
```

> نکته:
>
>برای خوانایی بیش‌تری اجزایی را که تابع یا متد برمی‌گرداند را در خط‌های جداگانه می‌نویسیم و پرانتزی به آن اضافه می‌کنیم. پس جاوا اسکریپت بعد از `return` سمی‌کالن نمی‌گذارد(و ما باید آن را بگذاریم).

هم اکنون دو پراپس از Board به Square می‌فرستیم: `value` و `onClick`. پراپس  `onClick` یک تابع است که Square می‌تواند هر وقت کلیک شد آن را اجرا کند. پس تغییرات زیر را در Square ایجاد می‌کنیم:

* جایگزین کردن `this.state.value` با `this.props.value` در متد `render` مربوط به Square
* جایگزین کردن `this.setState()` با `this.props.onClick()` در متد `render` مربوط به Square
* حذف `constructor` از Square چون که او دیگر مسیر بازی را ذخیره نمی‌کند

بعد از این تغییرات، کد کامپوننت Square باید شبیه به این باشد:

```javascript{1,2,6,8}
class Square extends React.Component {
  render() {
    return (
      <button
        className="square"
        onClick={() => this.props.onClick()}
      >
        {this.props.value}
      </button>
    );
  }
}
```

وقتی که یک Square کلیک شد تابع `onClick` که از Board می‌آید، صدا زده می‌شود. این‌جا مروری بر چگونگی بدست آمدن این که مروری می‌کنیم:

1. پراپ `onClick` در کامپوننت `<button>` که از پیش تعریف شده و DOM است برای ری‌اکت به این معناست که یک شنونده‌ی رویداد برای کلیک(click event listener) برای او تعریف کن.
2. وقتی که دکمه کلیک شد، ری‌اکت کنترل کننده‌ی رویداد `onClick` که در متد `render()` کامپوننت Square تعریف شده را صدا می‌زند.
3. کنترل کننده‌ی رویداد `this.props.onClick()` را صدا می‌زند. این پراپس از طرف Board تعریف شده بود.
4. از آنجایی که `Board، onClick={() => this.handleClick(i)}` را به Square فرستاده‌ایم، Square دستور `this.handleClick(i)` را در هنگام کلیک شدنش اجرا می‌کند.
5. چون هنوز متد `handleClick()` را نساخته‌ایم، کد ما کرش خواهد کرد. پس اگر الان روی یک مربع کلیک کنید خطایی شبیه به "this.handleClick is not a function" پدیدار می‌شود.


>نکته
>
>در `<button>` به دلیل اینکه یک کامپوننت از پیش ساخته شده(build-in) و DOM است، صفت `onClick` برایش معنای ویژه‌ای دارد(که یک کنترل کننده‌ی رویداد ایجاد برای کلیک ایجاد می‌کند). اما در کامپوننت‌های سفارشی مثل Square، نام‌گذاری‌اش دست شماست. ما می‌توانیم هر اسمی را به پراپس `onClick` یا متد `handleClick` بدهیم و کاملا هما کار انجام دهد. در ری‌اکت مرسوم است که برای پراپس‌هایی که نماینده‌ی یک رویداد هستند از `on[Event]` و برای توابعی که به یک رویداد رسیدگی می‌کنند از `handle[Event]` استفاده می‌شود.

همان طور که گفته شد اگر روی Square کلیک کنید به دلیل نبود متد `handleClick`، خطایی دریافت خواهید کرد. حالا زمان آن رسیده که آن را ایجاد کنیم:

```javascript{9-13}
class Board extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      squares: Array(9).fill(null),
    };
  }

  handleClick(i) {
    const squares = this.state.squares.slice();
    squares[i] = 'X';
    this.setState({squares: squares});
  }

  renderSquare(i) {
    return (
      <Square
        value={this.state.squares[i]}
        onClick={() => this.handleClick(i)}
      />
    );
  }

  render() {
    const status = 'Next player: X';

    return (
      <div>
        <div className="status">{status}</div>
        <div className="board-row">
          {this.renderSquare(0)}
          {this.renderSquare(1)}
          {this.renderSquare(2)}
        </div>
        <div className="board-row">
          {this.renderSquare(3)}
          {this.renderSquare(4)}
          {this.renderSquare(5)}
        </div>
        <div className="board-row">
          {this.renderSquare(6)}
          {this.renderSquare(7)}
          {this.renderSquare(8)}
        </div>
      </div>
    );
  }
}
```

**[مشاهده‌ی کد کامل](https://codepen.io/gaearon/pen/ybbQJX?editors=0010)**

بعد از انجام این تغییرات شما دوباره قادر خواهید بود با کلیک بر روی هر مربع، آن‌ها را پر کنید، شبیه چیزی که قبلا داشتیم. ولی این بار موقعیت بازی به جای Square در Board ذخیره می‌شود. و وقتی که state کامپوننت Board تغییر می‌کند، همه‌ی مربع‌ها به صورت اتوماتیک دوباره رندر گرفته می‌شوند. نگهداری حالت همه‌ی مربع‌ها در Board به ما اجازه می‌دهد که بعدا بتوانیم برنده را مشخص کنیم.

از آن جایی که Square دیگر state ندارد، در زمان نیاز مقدارها را از Board گرفته و در زمان رویداد کلیک، به Board اطلاع می‌دهد(و مقدار state‌ شان را تغییر می‌دهد). در اصطلاح ری‌اکت به Square **کامپوننت کنترل شده** می‌گویند زیرا که Board کنترل کامل بر روی او دارد.

به متد `handleClick` نگاه کنید. ما با فراخوانی متد `.slice()` یک کپی از آرایه‌ی `squares` درست کرده‌ایم و به جای تغییر مستقیم، کپی شده را بر روی آن جایگزین می‌کنیم. در بخش بعدی دلیل این کار را توضیح خواهیم داد.

### چرا جایگزینی؟ {#why-immutability-is-important}

همان طور که مشاهده کردید، در کد بالا، از آرایه‌ی squares کپی گرفته و آن را بر روی قبلی جایگزین کردیم. به این کار Immutability(البته در برنامه‌نویسی این عبارت به متغیرهای تغییر ناپذیر نیز گفته می‌شود) و در صورتی که تغییر مستقیم داده‌ها مان را تغییر می‌دادیم، mutability می‌گویند.

#### تغییر داده با Mutation(تغییر مستقیم) {#data-change-with-mutation}

```javascript
var player = {score: 1, name: 'Jeff'};
player.score = 2;
// اکنون player برابر {score: 2, name: 'Jeff'} است
// Now player is {score: 2, name: 'Jeff'}
```

#### تغییر داده بدون Mutation(تغییر غیرمستقیم) {#data-change-without-mutation}

```javascript
var player = {score: 1, name: 'Jeff'};

var newPlayer = Object.assign({}, player, {score: 2});
// در اینجا player تغییر نیافته و به جایش متغیر newPlayer برابر {score: 2, name: 'Jeff'} شده
// Now player is unchanged, but newPlayer is {score: 2, name: 'Jeff'}

// اما شما می‌توانید Spread Syntax نیز استفاده کنید:
var newPlayer = {...player, score: 2};
```

نتیجه هر دو یکسان است(البته در خصوص پروژه‌ی ما به دلیل ذکر شده در پایین، Mutation کار نخواهد کرد) اما Immutability فوایدی دارد که در زیر ذکر شده است.

#### ساخت امکانات پیچیده، آسان می‌شود {#complex-features-become-simple}

در روش تغییر ناپذیر، به آسانی میتوانیم نسخه‌ی قبلی داده‌مان را ذخیره کنیم. ولی در تغییر پذیر چون به صورت مستقیم داده‌ها را تغییر داده‌ایم، این امکان وجود ندارد(یا کمی سخت‌تر می‌شد). برای مثال در همین آموزش، امکانی را به نام "ماشین زمان" خواهیم ساخت که به کاربر اجازه می‌دهد به حرکت‌های قبلی برگردد و تاریخچه‌ی بازی را مطالعه کند. البته این آپشن تنها به منحصر به بازی‌ها نیست و در بسیاری از برنامه‌ها توانایی undo و redo وجود دارد.

#### تشخیص تغییرات {#determining-when-to-re-render-in-react}

تشخیص تغییرات در اشیایی که صورت مستقیم تغییر می‌کند بسیار سخت است(منظور از اشیاء همان object در برنامه‌نویسی شی گراست). در این تشخیص نیاز به کپی‌های نسخه‌ی قبلی آن و مقایسه‌ی تمام propertiesهای دو شئ جدید و قدیم داریم(به دلیل اینکه هر properties خود نیز می‌تواند حاوی یک properties دیگر باشد باید آن را به صورت درختی مقایسه کنیم). 

به مثال زیر دقت کنید.

```javascript
class nameclass {
 constructor() {
   this.firstname = "thatisnot";
   this.lastname = "youbusiness";
 }
}
class person {
 constructor() {
   this.name = nameclass()
   this.job = "Programmer"
 }
}
myobj1 = person()
myobj2 = person()
// حالا می‌خواهیم myobj1 و myobj2 را مقایسه کنیم.

console.log(myobj1 == myobj2)
// همیشه False برمی‌گرداند پس نمی‌توان برای مقایسه استفاده کرد
 
// برای مقایسه‌ی دو object نیاز به چیزی شبیه به این داریم:
if (myobj1.name.firstname == myobj2.name.firstname) && (myobj1.name.lastname == myob2.name.lastname) && (myobj1.job == myobj2.job) {
   console.log("myobj1 is equal to myobj2")
} else {
   console.log("myobj2 is not equal to myobj2")
}

```

اما تشخیص تغییرات در اشیاء غیر قابل تغییر به صورت قابل توجهی ساده‌تر است. اگر مکان حافظه‌ای که شئ مورد نظرمان در آن قرار دارد با نسخه‌ی قبلی تفاوت داشت، پس آن تغییر کرده، و حالا تنها زمانی که واقعا شئ مورد نظر تغییر کرده باشد نیاز است دو شیء را با هم مقایسه کنیم تا پارامترها تغییر کرده را دریابیم. بنابراین علاوه بر سادگی، در مصرف منابع نیز صرفه‌جویی می‌شود.

#### تشخیص زمان نیاز به رندر برای ری‌اکت {#determining-when-to-re-render-in-react}

فایده اصلی استفاده از Immutability امکان ساخت _pure components_ است. زیرا که تشخیص تغییرات در این نوع بسیار ساده است ری‌اکت می‌تواند زمانی که تغییری ایجاد شد آن را شناسایی کرده و کامپوننت‌های دچار تغییر را دوباره رندر می‌کند.

شما می‌توانید درباره‌ی متد `shouldComponentUpdate()` و چگونگی ساخت *pure components* از [اینجا](/docs/optimizing-performance.html#examples) اطلاعات کسب کنید. 

اگر کنجکاو هستید میتوانید در متد `handleClick` به جای کد قبلی عبارت `'this.state.squares[i] = 'X;` قرار دهید. مشاهده خواهید کرد بعد از فشردن مربع‌ها هیچ تغییری ایجاد نمی‌شود ولی اگر در تب components، قسمت DeveloperTools مرورگرتان رفته و روی Board کلیک کنید، خواهید دریافت state آن تغییر کرده اما به دلیل دوباره رندر نشدن، صفحه به همان صورت قبلی باقی مانده.

 همان طور که گفته شد تشخیص تغییرات در داده‌های Mutable بسیار سخت است و باعث کندی صفحه می‌شود. بنابر این ری‌اکت همیشه stateها را Immutable فرض می‌کند(تا در زمان تغییر کامپوننت‌ها را به‌روز کند) و به این دلیل است که در صورت تغییر دادن state به صورت مستقیم، ری‌اکت متوجه تغییر نمی‌شود. 


### کامپوننت تابعی {#function-components}

هم اکنون کامپوننت Square را به یک **کامپوننت تابعی(Function Components)** تبدیل می‌کنیم.

در ری‌اکت، کامپوننت تابعی راهی ساده برای ساخت کامپونننت‌های بدون state و آن‌هایی که تنها متد `render` دارد است. به صورت خلاصه برای ساخت کامپوننت‌های ساده و مختصر از کامپونت تابعی استفاده می‌کنیم. تنها کافی‌ست به جای ساخت کلاسی که از `React.Components` ارث می‌برد یک تابع بنویسیم که props را در ورودی دریافت و کد نیاز به رندر را برگرداند. نوشتن کامپوننت تابعی بسیار ساده‌تر از کلاس‌هاست و کامپوننت‌های زیادی را می‌توان به این صورت نوشت.

پس کلاس Square با این تابع جایگزین می‌کنیم:

```javascript
function Square(props) {
 return (
   <button className="square" onClick={props.onClick}>
     {props.value}
   </button>
 );
}
```

توجه داشته باشید که در این تبدیل نیاز است تمام `this.state`ها را با `state` جایگزین کنیم.

[مشاهده‌ی کد کامل](https://codepen.io/gaearon/pen/QvvJOv?editors=0010)

> نکته
>
> در زمان تبدیل Square به یک کامپوننت تابعی، ما همچنین `onClick={() => this.props.onClick()}` را کوتاه‌تراش `onClick={props.onClick}` تغییر دادیم (به نبود پرانتز در **هر دو طرف** دقت کنید)

### چرخش نوبت {#taking-turns}

ما اکنون نیاز داریم نقضی واضع در بازی را بر طرف کنیم: هیچگاه "O" روی تخته بازی مشخص نمی‌شود.

اولین حرکت را به صورت پیش‌فرض "X" قرار می‌دهیم. این کار می‌تواند با مقدار دادن اولیه یک state انجام شود. پس آن را در constructor کلاس Board قرار می‌دهیم.

```javascript{6}
class Board extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      squares: Array(9).fill(null),
      xIsNext: true,
    };
  }
```

هر وقت که مخاطب حرکتی را انجام می‌دهد، متغیر `xIsNext` وارون می‌گردد تا مشخص کند نوبت نفر بعدی‌ست. بعد از آن state بازی سیو می‌شود.

پس این تغییرات را در متد `handleClick` بورد انجام می‌دهیم تا در زمان کلیک آن را وارون کند.

```javascript{3,6}
  handleClick(i) {
    const squares = this.state.squares.slice();
    squares[i] = this.state.xIsNext ? 'X' : 'O';
    this.setState({
      squares: squares,
      xIsNext: !this.state.xIsNext,
    });
  }
```
با این تغییرات، با هر حرکت نوبت "X"ها و "O"ها تغییر می‌کند و عوض می‌شود. میتوانید امتحان کنید.

بیایید متن "status" را هم در متد `render` بورت عوض کنیم تا نشان دهد این حرکت نوبت کیست.

```javascript{2}
  render() {
    const status = 'Next player: ' + (this.state.xIsNext ? 'X' : 'O');

    return (
      // the rest has not changed
```


بعد از این تغییرات، کلاس بوردتان باید به این صورت باشد:


```javascript{6,11-16,29}
class Board extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      squares: Array(9).fill(null),
      xIsNext: true,
    };
  }

  handleClick(i) {
    const squares = this.state.squares.slice();
    squares[i] = this.state.xIsNext ? 'X' : 'O';
    this.setState({
      squares: squares,
      xIsNext: !this.state.xIsNext,
    });
  }

  renderSquare(i) {
    return (
      <Square
        value={this.state.squares[i]}
        onClick={() => this.handleClick(i)}
      />
    );
  }

  render() {
    const status = 'Next player: ' + (this.state.xIsNext ? 'X' : 'O');

    return (
      <div>
        <div className="status">{status}</div>
        <div className="board-row">
          {this.renderSquare(0)}
          {this.renderSquare(1)}
          {this.renderSquare(2)}
        </div>
        <div className="board-row">
          {this.renderSquare(3)}
          {this.renderSquare(4)}
          {this.renderSquare(5)}
        </div>
        <div className="board-row">
          {this.renderSquare(6)}
          {this.renderSquare(7)}
          {this.renderSquare(8)}
        </div>
      </div>
    );
  }
}
```

**[مشاهده‌ی کد کامل](https://codepen.io/gaearon/pen/KmmrBy?editors=0010)**

### تعیین برنده {#declaring-a-winner}

حالا که به نوبت بازیکن‌ها عوض می‌شود، وقت آن است زمانی که کسی برنده می‌شود او را مشخص کرده و دیگر اجاره به تغییر بازی ندهد. این تابع کمک‌گر را در آخر فایل‌تان کپی‌پیست کنید:

```javascript
function calculateWinner(squares) {
  const lines = [
    [0, 1, 2],
    [3, 4, 5],
    [6, 7, 8],
    [0, 3, 6],
    [1, 4, 7],
    [2, 5, 8],
    [0, 4, 8],
    [2, 4, 6],
  ];
  for (let i = 0; i < lines.length; i++) {
    const [a, b, c] = lines[i];
    if (squares[a] && squares[a] === squares[b] && squares[a] === squares[c]) {
      return squares[a];
    }
  }
  return null;
}
```

این تابع یک آرایه‌ی مقادیر ۹ مربع را دریافت کرده، برای یکی از مقادیر `'X'` یا `'O'` و یا `null` را بر اساس مقدار دریافت شده بر می‌گرداند.

برای چک کردن برنده(و اینکه اصلا کسی برنده شده یا نه) در متد `render` بُرد `calculateWinner(squares)` را صدا می‌زنیم. اگر کسی برنده شده باشد، می‌توانیم متنی مشابه "Winner: X" و یا "Winner: O" روی صفحه نمایش دهیم.

پس معرف state را در متد render بورد با این کد جایگزین می‌کنیم:

```javascript{2-8}
  render() {
    const winner = calculateWinner(this.state.squares);
    let status;
    if (winner) {
      status = 'Winner: ' + winner;
    } else {
      status = 'Next player: ' + (this.state.xIsNext ? 'X' : 'O');
    }

    return (
      // بقیه تغییری نمی‌کند
```

حالا به می‌توانیم آسانی تغییراتی را در متد `handleClick` بورد ایجاد کنیم که کلیکی که بر مربع از قبل پر شده و حرکت بعد از برنده شدن کسی را نادیده بگیرد.

```javascript{3-5}
  handleClick(i) {
    const squares = this.state.squares.slice();
    if (calculateWinner(squares) || squares[i]) {
      return;
    }
    squares[i] = this.state.xIsNext ? 'X' : 'O';
    this.setState({
      squares: squares,
      xIsNext: !this.state.xIsNext,
    });
  }
```

**[مشاهده‌ی کد کامل](https://codepen.io/gaearon/pen/LyyXgK?editors=0010)**

تبریک، هم اکنون یک بازی tic-tac-toe ساخته‌اید که کاملا کار می‌کند و از همه مهم‌تر اینکه مفاهیم اصلی ری‌اکت را آموخته‌اید پس می‌توان گفت برنده‌ی اصلی این بازی **شمایید**.

## اضافه کرده قابلیت ماشین زمان {#adding-time-travel}

در مرحله‌ی آخر می‌خواهیم امکان برگرشت به حرکت‌های قبلی را در بازی پیاده سازی کنیم.

### ذخیره‌ی تاریخچه‌ی حرکت‌ها {#storing-a-history-of-moves}

اگر در گذشته آرایه‌ی `squares` را به صورت تغییر پذیر تعریف کرده بودیم، هم اکنون پیاده‌سازی ماشین زمان بسیار سخت می‌شد به همین خاطر با استفاده `slice()` یک کپی از آرایه‌ی `squares` برای هر حرکت می‌گرفتیم و با آن [به صورت تغییر ناپذیر رفتار می‌کردیم](#why-immutability-is-important). این کار اجازه می‌دهد تمامی نسخه‌های قبلی آن را داشته باشیم و بتوانیم در حرکت‌های انجام شده حرکت کنیم.

ما تمام نسخه‌های قبلی sqauares را در آرایه‌ای دیگر به نام `history` ذخیره می‌کنیم. پس آرایه‌ی `history` تمامی state بورد را از ابتدا تا آخرین حرکت را دربر خواهد داشت و چیزی شبیه به این خواهد بود:

```javascript
history = [
  // Before first move
  {
    squares: [
      null, null, null,
      null, null, null,
      null, null, null,
    ]
  },
  // After first move
  {
    squares: [
      null, null, null,
      null, 'X', null,
      null, null, null,
    ]
  },
  // After second move
  {
    squares: [
      null, null, null,
      null, 'X', null,
      null, null, 'O',
    ]
  },
  // ...
]
```

اکنون باید تصمیم بگیریم که آرایه‌ی `history` در state کدام کامپوننت باید قرار گیرد.

### بالا بردن دوباره‌ی state {#lifting-state-up-again}

ما نیاز داریم کامپوننت سطح بالای Game لیست تمامی حرکت‌های گذشته را نمایش دهد. برای این کار او نیاز آرایه‌ی `history` نیاز دارد. پس بهتر است ما آن را در خود Game قرار دهیم.

قرار دادن `history` به صورت state در کامپوننت Game به ما اجازه می‌دهد تا استیت(state) `squares` را از فرزندش یعنی از Board حذف کنیم. دقیقا شبیه به بخش ["بالا بردن state"](#lifting-state-up) که از Square به Board انتقال داده بودیم، الآن آن را از Board به کامپوننت بالا رده‌ یعنی Game انتقال می‌دهیم. این کار به Game اجازه می‌دهد تا کنترل کامل بر روی داده‌ Board داشته باشد و به او بگوید تا حرکت قبلی را از `history` رندر کند.

ابتدا نیاز داریم state اولیه را در constructor کامپوننت Game مقدار دهی کنیم:

```javascript{2-10}
class Game extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      history: [{
        squares: Array(9).fill(null),
      }],
      xIsNext: true,
    };
  }

  render() {
    return (
      <div className="game">
        <div className="game-board">
          <Board />
        </div>
        <div className="game-info">
          <div>{/* status */}</div>
          <ol>{/* TODO */}</ol>
        </div>
      </div>
    );
  }
}
```

در مرحله‌ی بعد نیاز داریم که Board پراپ‌های `onClick` و `squares` را از Game دریافت کنند. از آنجایی که ما یک کنترل کننده‌ی کلیک برای تعداد زیادی Square داریم، نیاز داریم تا مکان هر یک از آن‌ها را نیز به کنترلر `onClick` بفرستیم تا نشان دهد که کدام مربع کلیک شده است.

در اینجا چند مرحله برای تغییر دادن کامپونت Board وجود دارد:

* حذف کردن متد constructor از بورد
* جایگزین کردن `this.state.squares[i]` با `this.props.squares[i]`
* جایگزین کردن `this.handleClick(i)` با `this.props.onClick(i)` در متد `renderSquare` بورد.

  هم‌اکنون کلاس Board باید به این صورت باشد:

```javascript{17,18}
class Board extends React.Component {
  handleClick(i) {
    const squares = this.state.squares.slice();
    if (calculateWinner(squares) || squares[i]) {
      return;
    }
    squares[i] = this.state.xIsNext ? 'X' : 'O';
    this.setState({
      squares: squares,
      xIsNext: !this.state.xIsNext,
    });
  }

  renderSquare(i) {
    return (
      <Square
        value={this.props.squares[i]}
        onClick={() => this.props.onClick(i)}
      />
    );
  }

  render() {
    const winner = calculateWinner(this.state.squares);
    let status;
    if (winner) {
      status = 'Winner: ' + winner;
    } else {
      status = 'Next player: ' + (this.state.xIsNext ? 'X' : 'O');
    }

    return (
      <div>
        <div className="status">{status}</div>
        <div className="board-row">
          {this.renderSquare(0)}
          {this.renderSquare(1)}
          {this.renderSquare(2)}
        </div>
        <div className="board-row">
          {this.renderSquare(3)}
          {this.renderSquare(4)}
          {this.renderSquare(5)}
        </div>
        <div className="board-row">
          {this.renderSquare(6)}
          {this.renderSquare(7)}
          {this.renderSquare(8)}
        </div>
      </div>
    );
  }
}
```

همچنین باید در متد `render` کامپوننت Game تغییراتی بدهیم تا از آخرین عضو متغیر `history` برای مشخص کردن و نمایش حالت بازی استفاده کند:

```javascript{2-11,16-19,22}
  render() {
    const history = this.state.history;
    const current = history[history.length - 1];
    const winner = calculateWinner(current.squares);

    let status;
    if (winner) {
      status = 'Winner: ' + winner;
    } else {
      status = 'Next player: ' + (this.state.xIsNext ? 'X' : 'O');
    }

    return (
      <div className="game">
        <div className="game-board">
          <Board
            squares={current.squares}
            onClick={(i) => this.handleClick(i)}
          />
        </div>
        <div className="game-info">
          <div>{status}</div>
          <ol>{/* TODO */}</ol>
        </div>
      </div>
    );
  }
```

از آنجایی که Game حالت بازی را رندر می‌کند. می‌توانیم کدهای اضافی را از متد `render` بورد پاک کنیم. بعد از پاکسازی آن، باید به این صورت در بیاید:

```js{1-4}
  render() {
    return (
      <div>
        <div className="board-row">
          {this.renderSquare(0)}
          {this.renderSquare(1)}
          {this.renderSquare(2)}
        </div>
        <div className="board-row">
          {this.renderSquare(3)}
          {this.renderSquare(4)}
          {this.renderSquare(5)}
        </div>
        <div className="board-row">
          {this.renderSquare(6)}
          {this.renderSquare(7)}
          {this.renderSquare(8)}
        </div>
      </div>
    );
  }
```

در نهایت، ما نیاز داریم متد `handleClick` را از Board به Game منتقل کرده و همچنین کمی آن را تغییر دهیم زیرا که ساختار state کامپونتت Game کمی متفاوت است. در متد `handleClick` کامپوننت Game نیز عضو جدید را به آرایه‌ی `history` می‌چسبانیم.

```javascript{2-4,10-12}
  handleClick(i) {
    const history = this.state.history;
    const current = history[history.length - 1];
    const squares = current.squares.slice();
    if (calculateWinner(squares) || squares[i]) {
      return;
    }
    squares[i] = this.state.xIsNext ? 'X' : 'O';
    this.setState({
      history: history.concat([{
        squares: squares,
      }]),
      xIsNext: !this.state.xIsNext,
    });
  }
```

> نکته
> 
> برخلاف متد `push()` آرایه‌ها که احتمالا با آن بیشتر آشنایی دارید، متد `concat()` آرایه‌ی اصلی را تغییر نمی‌دهد، پس ما آن را به `push()` ترجیح می‌دهیم.

در این جا، Board تنها به توابع `renderSquare` و `render` نیاز دارد و حالت بازی و متد `handleClick` باید در کامپوننت Game باشد.

**[مشاهده‌ی کد کامل](https://codepen.io/gaearon/pen/EmmOqJ?editors=0010)**

### نمایش حرکت‌های قبلی به کابر {#showing-the-past-moves}

از آن جایی که ما تمامی حرکات را ضبط می‌کنیم، به آسانی می‌توانیم این اجازه را به کاربر بدهیم تا بین حرکاتش حرکت کند.

همان طور که قبلا یاد گرفتید، هر کامپوننت توی ری‌اکت در اصل یک شئ(object) توی جاوا اسکریپت است و می‌تونیم از آن‌ها در سرتاسر برنامه به عنوان یک شئ استفاده کنیم. پس برای رندر کردن تعدادی از کامپوننت می‌توانیم از آرایه‌ای شامل کامپوننت‌های ری‌اکت درست کنیم.

در جاوا اسکریپت، آرایه‌ها [متدی به نام map](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map) دارند که به صورت گسترده برای مپ کردن داده به داده‌ای دیگر استفاده می‌شود. اگر با مفهوم مپ کردن آشنایی ندارید، نگران نباشید اینجا یک مثال وجود دارد:

```js
const numbers = [1, 2, 3];
const doubled = numbers.map(x => x * 2); // [2, 4, 6]
```

در مثال بالا، ماشین از ابتدای لیست مورد نظر شروع می‌کند و آن را درون تابعی دلخواه را درون تابع داده شده قرار می‌دهد (در اینجا این تابع `x => x * 2` است که یک مقدار گرفته و دو برابر آن در خروجی بر می‌گرداند). سپس ماشین مقدار برگردانده شده توسط تابع را بر روی مقدار اولیه جایگزین می‌کند. و به سراغ مقدار بعدی می‌رود. توجه داشته باشید که آرایه‌ی یا لیست ورودی ما تغییر نخواهد کرد و نتیجه برگردانده خواهد شد.

تابع مورد نظر ما می‌تواند تا ۳ مقدار بگیرد(۱ مقدار الزامی و ۲ مقدار دیگر اختیاری‌است) که به ترتیب:

1. عضو مورد نظر لیست یا آرایه
2. مکان یا اندیس عضو مورد نظر (دقت کنید که صفر شروع می‌شود)
3. خود آرایه‌ای که عضو در آن قرار دارد

برای اطلاعات بیش‌تر می‌توانید به [اینجا](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map) رجوع کنید.

با استفاده از مپ کردن می‌توانیم آرایه‌ی `history` را به کامپوننت‌های ری‌اکت تبدیل کنیم که دکمه‌هایی را برای برگشت به حرکت‌های قبلی دربر می‌دارند.

بیایید در متد `render` کامپوننت Game، بر روی `history` مپ کنیم:

```javascript{6-15,34}
  render() {
    const history = this.state.history;
    const current = history[history.length - 1];
    const winner = calculateWinner(current.squares);

    const moves = history.map((step, move) => {
      const desc = move ?
        'Go to move #' + move :
        'Go to game start';
      return (
        <li>
          <button onClick={() => this.jumpTo(move)}>{desc}</button>
        </li>
      );
    });

    let status;
    if (winner) {
      status = 'Winner: ' + winner;
    } else {
      status = 'Next player: ' + (this.state.xIsNext ? 'X' : 'O');
    }

    return (
      <div className="game">
        <div className="game-board">
          <Board
            squares={current.squares}
            onClick={(i) => this.handleClick(i)}
          />
        </div>
        <div className="game-info">
          <div>{status}</div>
          <ol>{moves}</ol>
        </div>
      </div>
    );
  }
```

**[مشاهده‌ی کد کامل](https://codepen.io/gaearon/pen/EmmGEa?editors=0010)**

بدین صورت، برای حرکت در بازی یک `<li>` درست می‌شود که دکمه‌ای را دربر دارد. کنترلر `onClick` موجود در این دکمه متد `this.justTo()` را صدا می‌زند که هنوز آن را پیاده سازی نکرده‌ایم. ما در حال حاضر باید لیستی از حرکت‌های بازی و این هشداری را در developer tools مرورگرمان ببینیم:

> Warning: Each child in an array or iterator should have a unique “key” prop. Check the render method of “Game”.

حال باید ببینیم دلیل این هشدار چیست

### قرار دادن یک کلید {#picking-a-key}

زمانی که یک لیست را رندر می‌کنیم، ری‌اکت اطلاعاتی را درباره‌ی آن جمع‌آوری می‌کند. زمانی که نیاز است این لیست به روز شود، ری‌اکت نیاز دارد تا تشخیص دهد کدام یکی تغییر کرده. ما باید بتوانیم تا به لیست‌مان عضوی اضافه یا حذف و یا مرتب و آپدیت کنیم.

فرض کنید این لیست را:

```html
<li>Alexa: 7 tasks left</li>
<li>Ben: 5 tasks left</li>
```

به این لیست تبدیل کنیم:

```html
<li>Ben: 9 tasks left</li>
<li>Claudia: 8 tasks left</li>
<li>Alexa: 5 tasks left</li>
```

در این‌گونه موارد یک انسان به آسانی می‌تواند بگویید: جای Alexa و Ben عوض شده و Claudia نیز به این لیست اضافه شده. اما از آن جایی که ری‌اکت که یک برنامه‌ی کامپیوتری است نمی‌تواند بفهمد چه چیزی اضافه شده است. پس نیاز داریم برای این که هر عضو از دیگری متمایز شود، برایشان یک ویژگی *key* تعریف کنیم که مخصوص خودش باشد(منحصر به فرد باشد). در این جا یک گزینه می‌تواند استفاده از مقادیر `alexa` , `ben` و یا `claudia` باشد اما اگر این اطلاعات از یک دیتابیس است می‌توانیم آی‌دی(شناسه) آن‌ها را به عنوان key استفاده کنیم.

```html
<li key={user.id}>{user.name}: {user.taskCount} tasks left</li>
```

زمانی که کامپوننت دوباره رندر می‌شود، ری‌اکت مقدار key هر عضو را گرفته و با نسخه‌ی قبلی لیست مقایسه می‌کند، اگر این key وجود از قبل وجود نداشت، آن را می‌سازد. و اگر لیست جدید یک key را دربر نداشت، ری‌اکت کامپوننت قبلی را پاک می‌کند. و اگر دو key در هر دو لیست وجود داشتند(یعنی که یکی از آن‌ها جابه‌جا شده‌اند) پس آن را حرکت می‌دهد. کلیدها هویت هر کامپوننت را به ری‌اکت نشان می‌دهند و کمک می‌کنند که stateهای آن بعد از دوباره رندر شدن تغییر نکنند. اگر key یک کامپوننت تغییر کند، آن کامپوننت پاک خواهد شد و دوباره با یک state جدید ایجاد می‌شود.

`key`(به علاوه‌ی `ref` که یک فیچر پیشرفته‌ست) یک property خاص و رزرو شده در ری‌اکت‌اند. این به معناست که شاید key شبیه به یک props باشد اما شما نمی‌توانید از درون کامپوننت با استفاده از `this.props.key` به آن دسترسی پیدا کنید. ری‌اکت به صورت اتوماتیک از ویژگی key برای آپدیت کامپوننت‌ها استفاده می‌کند و یک کامپوننت هیچ گاه نمی‌تواند از مقدار key خود مطلع شود.

**شدیدا توصیه می‌شود که اگر با لیست‌های داینامیک(تغییر می‌کنند و جا به جا می‌شوند) کار می‌کنید از key مناسب برای هر لیست استفاده کنید.** اگر این کار انجام نشود امکان دارد داده‌های درون کامپوننت‌هاتان پاک شوند.

اگر در لیست‌ها ویژگی key را مقدار دهی نکنید، ری‌اکت هشداری خواهد داد و به صورت پیش‌فرض از مکان(اندیس آرایه) آن لیست به عنوان key استفاده می‌کند. و این کار می‌تواند بسیار در به جابه‌جا، اضافه یا حذف عضو مشکل‌ساز باشد. توجه داشته باشید که هرچند که می‌توانیم با قرار دادن key={i} (i اندیس آرایه است) هشدار از بین ببریم اما مشکل همچنان باقی‌ست.

نیازی به خاص بودن کلیدها در کل فایل نیست و تنها خاص بودن بین برادر/خواهرهایشان کفایت می‌کند.

### پیاده‌سازی ماشین زمان {#implementing-time-travel}

در تاریخچه‌ی بازی، هر حرکت گذشته یک شناسه‌ی منحصر به فرد دارد و آن نیز مرتبه‌ی آن حرکت است. مرتبه‌ی حرکت‌ها هیچ وقت از وسط حذف یا اضافه یا حرکت نمی‌کنند. پس استفاده از مرتبه‌ی حرکت به عنوان key امن است و مشکلی ندارد.

برای اینکه هشدار نبود key از بین برود در متد `render` کامپوننت Game، می‌توانیم key را برابر `{move}` بگذاریم.


```js{6}
    const moves = history.map((step, move) => {
      const desc = move ?
        'Go to move #' + move :
        'Go to game start';
      return (
        <li key={move}>
          <button onClick={() => this.jumpTo(move)}>{desc}</button>
        </li>
      );
    });
```

**[مشاهده‌ی کد کامل](https://codepen.io/gaearon/pen/PmmXRE?editors=0010)**

با کلیک بر روی هر یک از دکمه‌ها، خطایی به معنای نبود متد `jumpTo` ظاهر می‌شود. بعدا این متد را نیر خواهیم ساخت اما قبل از آن نیاز داریم تا یک state به نام `stepNumber` برای نمایش تعداد گام‌هایی که حرکت انجام گرفته تعریف کنیم.

ابتدا، استیت `stepNumber: 0` را به منظور دادن مقدار اولیه در `constructor` کامپوننت Game اضافه می‌کنیم.

```js{8}
class Game extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      history: [{
        squares: Array(9).fill(null),
      }],
      stepNumber: 0,
      xIsNext: true,
    };
  }
```

در مرحله‌ی بعد متد `jumpTo` را به منظور آپدیت کردن `stepNumber` می‌سازیم. و همچنین برای اینکه نوبت افراد به‌هم نخورد، اگر گام مورد نظر زوج بود متغیر `xIsNext` برابر true می‌کنیم.

```javascript{5-10}
  handleClick(i) {
    // this method has not changed
  }

  jumpTo(step) {
    this.setState({
      stepNumber: step,
      xIsNext: (step % 2) === 0,
    });
  }

  render() {
    // این متد تغییری نمی‌کند
  }
```

اکنون نیاز داریم زمانی که کاربر به عقب بر می‌گردد و حرکتی انجام می‌دهد، حرکت‌های ذخیره شده‌ی بعد از آن گام، پاک شوند. به همین دلیل در متد `handleClick` عبارت `this.state.history` را با `this.state.history.slice(0, this.state.stepNumber + 1)` جایگزین می‌کنیم تا اگر تعداد عضوهای متغیر `history` بیش‌تر از گام‌ها(به علاوه‌ی یک صفحه‌ی خالی که در ابتدای بازی به صورت پیش‌فرض در آن وجود دارد) بود، بعد از آن را پاک کند(بعدا متغیر محلی `history` بر روی `this.state.history` از طریق متد `setState` جایگزین خواهد شد).

هم اکنون استیت `stepNumber` با کلیک بر روی دکمه‌های مخصوص برگشت به عقب تغییر می‌کند، اما ما نیاز داریم زمانی که کاربر در بازی حرکتی انجام می‌دهد نیز این استیت تغییر کند. پس در زمان صدا زدن متد `setState` آرگمان `stepNumber: history.length` را نیز قرار می‌دهیم. این کار باعث می‌شود بعد از برگشتن به عقب و انجام یک حرکت دوباره همان حرکت را انجام ندهیم(برای مثال اگر هرچه قدر حرکتی انجام دهیم روی همان شماره می‌ماند و دوباره همان حرکت قبلی را برایمان نمایش می‌دهد). البته اگر به جای این آرگمان می‌توانستیم از `stepNumber: this.state.stepNumber + 1` نیز استفاده کنیم.


```javascript{2,13}
  handleClick(i) {
    const history = this.state.history.slice(0, this.state.stepNumber + 1);
    const current = history[history.length - 1];
    const squares = current.squares.slice();
    if (calculateWinner(squares) || squares[i]) {
      return;
    }
    squares[i] = this.state.xIsNext ? 'X' : 'O';
    this.setState({
      history: history.concat([{
        squares: squares
      }]),
      stepNumber: history.length,
      xIsNext: !this.state.xIsNext,
    });
  }
```


در نهایت متد `render` کامپوننت Game را تصحیح می‌کنیم به جای رندر کردن آخرین گام، گام درست را بر پایه‌ی `stepNumber` رندر کند.


```javascript{3}
  render() {
    const history = this.state.history;
    const current = history[this.state.stepNumber];
    const winner = calculateWinner(current.squares);

    // بقیه بدون تغییر باقی می‌ماند
```

حالا اگر روی هر مرحله موجود روی تارخچه‌ی بازی کلیک کنیم، صفحه‌ی tic-tac-toe سریعا آپدیت شده و به ما اتفاقاتی که در آن گام افتاده را نشان می‌دهد.

**[مشاهده‌ی کد کامل](https://codepen.io/gaearon/pen/gWWZgR?editors=0010)**

### جمع‌بندی {#wrapping-up}

به شما تبریک می‌گوییم زیرا یک بازی tic-tac-toe ساختید که:
* اجازه می‌دهد بازی کنید
* برنده را نمایش می‌دهد
* روند بازی را ذخیره می‌کند
* و می‌گذارد کاربر تاریخچه‌ی بازی را بررسی و به گام‌های انجام داده‌اش برگردد

بسیار خب، امیدواریم درک خوبی از نحوه‌ی کارکرد با ری‌اکت به دست آورده باشید.

اگر وقت اضافه دارید و یا می‌خواهید مهارت خودتان را در ری‌اکت بسنجید، اینجا چند ایده برای بهبود این بازی وجود دارد که از راحت به سخت مرتب شده‌اند:

1. نمایش مکان حرکت انجام شده در لیست تاریچه‌ی حرکات
2. درشت شدن(Bold) شدن حرکت جاری در لیست حرکات
3. بازنویسی Board، تا از دو حلقه(مثل for یا while) به جای نوشتن کامل مربع‌ها استفاده کند.
4. درست کردن یک دکمه که حرکات را به دو دسته‌ی صعودی(بالا رونده) و نزولی(پایین رونده) تقسیم کند.
5. وقتی که کسی برنده شد، سه مربع که باعث این برد بودند را برجسته کند.
6. اگر کسی برنده نشد، یک پیام به کاربر به نمایش داده و بین دو بازیکن قرعه‌کشی کند.

در طول این آموزش با مفاهیم اصلی ری‌اکت همچون المان‌ها، کامپوننت‌ها، props و state آشنا شدید. برای اطلاع بیش‌تر درباره هر یک از موضوعات به [مستندات ری‌اکت](/docs/hello-world.html) و برای اطلاع بیش‌تر از انواع کامپوننت‌‌ها به [این قسمت](/docs/react-component.html) رجوع کنید.


بر گرفته از [نسخه‌ی انگلیسی](https://reactjs.org/tutorial/tutorial.html) - همراه با تغییرات برای درک بهتر مطالب توسط پارسی زبانان عزیز - مترجم اصلی: امیرمهدی نژادشمسی

**موفق باشید**




     
