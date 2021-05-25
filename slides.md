---
theme: apple-basic
class: text-center
layout: intro-image
image: https://source.unsplash.com/collection/94734566/1920x1080
---

# JavaScriptとNode.js入門

By @takafumikobayashi

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 p-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Press Space for next page <carbon:arrow-right class="inline"/>
  </span>
</div>

---

# What is Slidev?

Slidev is a slides maker and presenter designed for developers, consist of the following features

- 📝 **Text-based** - focus on the content with Markdown, and then style them later
- 🎨 **Themable** - theme can be shared and used with npm packages
- 🧑‍💻 **Developer Friendly** - code highlighting, live coding with autocompletion
- 🤹 **Interactive** - embedding Vue components to enhance your expressions
- 🎥 **Recording** - built-in recording and camera view
- 📤 **Portable** - export into PDF, PNGs, or even a hostable SPA
- 🛠 **Hackable** - anything possible on a webpage

<br>
<br>

Read more about [Why Slidev?](https://sli.dev/guide/why)

<!--
You can have `style` tag in markdown to override the style for the current page.
Learn more: https://sli.dev/guide/syntax#embedded-styles
-->

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent; 
  -moz-text-fill-color: transparent;
}
</style>

---

# Navigation

Hover on the bottom-left corner to see the navigation's controls panel, [learn more](https://sli.dev/guide/navigation.html)

### Keyboard Shortcuts

|     |     |
| --- | --- |
| <kbd>right</kbd> / <kbd>space</kbd>| next animation or slide |
| <kbd>left</kbd> | previous animation or slide |
| <kbd>up</kbd> | previous slide |
| <kbd>down</kbd> | next slide |

<!-- https://sli.dev/guide/animations.html#click-animations -->
<img
  v-click
  class="absolute -bottom-9 -left-7 w-80 opacity-50"
  src="https://sli.dev/assets/arrow-bottom-left.svg"
/>
<p v-after class="absolute bottom-23 left-45 opacity-30 transform -rotate-10">Here!</p>

---
layout: image-right
image: https://source.unsplash.com/collection/94734566/1920x1080
---

# Code

Use code snippets and get the highlighting directly!

<!-- https://sli.dev/guide/syntax.html#line-highlighting -->

```ts {all|2|1-6|9|all}
interface User {
  id: number
  firstName: string
  lastName: string
  role: string
}

function updateUser(id: number, update: User) {
  const user = getUser(id)
  const newUser = {...user, ...update}  
  saveUser(id, newUser)
}
```

<arrow v-click="3" x1="400" y1="420" x2="230" y2="330" color="#564" width="3" arrowSize="1" />

---

# Components

<div grid="~ cols-2 gap-4">
<div>

You can use Vue components directly inside your slides.

We have provided a few built-in components like `<Tweet/>` and `<Youtube/>` that you can use directly. And adding your custom components is also super easy.

```html
<Counter :count="10" />
```

<!-- ./components/Counter.vue -->
<Counter :count="10" m="t-4" />

Check out [the guides](https://sli.dev/builtin/components.html) for more.

</div>
<div>

```html
<Tweet id="1390115482657726468" />
```

<Tweet id="1390115482657726468" scale="0.65" />

</div>
</div>


---
class: px-20
---

# Themes

Slidev comes with powerful theming support. Themes are able to provide styles, layouts, components, or even configurations for tools. Switching between themes by just **one edit** in your frontmatter:

<div grid="~ cols-2 gap-2" m="-t-2">

```yaml
---
theme: default
---
```

```yaml
---
theme: seriph
---
```

<img border="rounded" src="https://github.com/slidevjs/themes/blob/main/screenshots/theme-default/01.png?raw=true">

<img border="rounded" src="https://github.com/slidevjs/themes/blob/main/screenshots/theme-seriph/01.png?raw=true">

</div>

Read more about [How to use a theme](https://sli.dev/themes/use.html) and
check out the [Awesome Themes Gallery](https://sli.dev/themes/gallery.html).

---
preload: false
---

# Animations

Animations are powered by [@vueuse/motion](https://motion.vueuse.org/).

```html
<div
  v-motion
  :initial="{ x: -80 }"
  :enter="{ x: 0 }">
  Slidev
</div>
```

<div class="w-60 relative mt-6">
  <div class="relative w-40 h-40">
    <img
      v-motion
      :initial="{ x: 800, y: -100, scale: 1.5, rotate: -50 }"
      :enter="final"
      class="absolute top-0 left-0 right-0 bottom-0"
      src="https://sli.dev/logo-square.png"
    />
    <img
      v-motion
      :initial="{ y: 500, x: -100, scale: 2 }"
      :enter="final"
      class="absolute top-0 left-0 right-0 bottom-0"
      src="https://sli.dev/logo-circle.png"
    />
    <img
      v-motion
      :initial="{ x: 600, y: 400, scale: 2, rotate: 100 }"
      :enter="final"
      class="absolute top-0 left-0 right-0 bottom-0"
      src="https://sli.dev/logo-triangle.png"
    />
  </div>

  <div 
    class="text-5xl absolute top-14 left-40 text-[#2B90B6] -z-1"
    v-motion
    :initial="{ x: -80, opacity: 0}"
    :enter="{ x: 0, opacity: 1, transition: { delay: 2000, duration: 1000 } }">
    Slidev
  </div>
</div>

<!-- vue script setup scripts can be directly used in markdown, and will only affects current page -->
<script setup lang="ts">
const final = {
  x: 0,
  y: 0,
  rotate: 0,
  scale: 1,
  transition: {
    type: 'spring',
    damping: 10,
    stiffness: 20,
    mass: 2
  }
}
</script>

<div
  v-motion
  :initial="{ x:35, y: 40, opacity: 0}"
  :enter="{ y: 0, opacity: 1, transition: { delay: 3500 } }">

[Learn More](https://sli.dev/guide/animations.html#motion)

</div>

---

# LaTeX

LaTeX is supported out-of-box powered by [KaTeX](https://katex.org/).

<br>

Inline $\sqrt{3x-1}+(1+x)^2$

Block
$$
\begin{array}{c}

\nabla \times \vec{\mathbf{B}} -\, \frac1c\, \frac{\partial\vec{\mathbf{E}}}{\partial t} &
= \frac{4\pi}{c}\vec{\mathbf{j}}    \nabla \cdot \vec{\mathbf{E}} & = 4 \pi \rho \\

\nabla \times \vec{\mathbf{E}}\, +\, \frac1c\, \frac{\partial\vec{\mathbf{B}}}{\partial t} & = \vec{\mathbf{0}} \\

\nabla \cdot \vec{\mathbf{B}} & = 0

\end{array}
$$

<br>

[Learn more](https://sli.dev/guide/syntax#latex)

---

# Diagrams

You can create diagrams / graphs from textual descriptions, directly in your Markdown.

<div class="grid grid-cols-2 gap-4 pt-4 -mb-6">

```mermaid {scale: 0.9}
sequenceDiagram
    Alice->John: Hello John, how are you?
    Note over Alice,John: A typical interaction
```

```mermaid {theme: 'neutral', scale: 0.8}
graph TD
B[Text] --> C{Decision}
C -->|One| D[Result 1]
C -->|Two| E[Result 2]
```

</div>

[Learn More](https://sli.dev/guide/syntax.html#diagrams)


---
layout: center
class: text-center
---

# Learn More

[Documentations](https://sli.dev) / [GitHub Repo](https://github.com/slidevjs/slidev)

---
layout: intro
---
# How to write JavaScript
by kobatch

---
layout: image-right
image: https://source.unsplash.com/collection/94734566/1920x1080
---

# 変数
  
* ここではJavaScriptで使われる変数とその特徴について学びます。

---

## 特徴と違いまとめ

変数が有効となる範囲（スコープ）と再宣言、再代入可能かがポイント

|     |     |     |
| --- | --- | --- |
|<h2>const</h2> |ブロックスコープ|再宣言不可 / 再代入不可|
|<h2>let</h2>|ブロックスコープ|再宣言不可 / <b>再代入可能</b>|
|<h2>var</h2>|<b>関数スコープ</b>|<b>再宣言可能</b> / <b>再代入可能</b>|

<style>
b {
  color: #dc143c
}
</style>

---
class: px-20
---

# const

再定義、再代入による値の変更が不可能

<div grid="~ cols-2 gap-2" m="-t-2">

```ts {all|1|5}
const a = 1;

console.log(a);

a = 2;

```

```bash
# 結果
1

"TypeError: Assignment to constant variable.
...
```

</div>

---
class: px-20
---

# let

ES6から新たに導入された変数宣言    
**ブロックスコープ** でのローカル変数、同一スコープ内で再代入も可能
  

<div grid="~ cols-2 gap-2" m="-t-2">

```ts {all|1|3-7|1,9}
let b = 1;

if (b === 1) {
  let b = 2;
  b = b + 3
  console.log(b)
};

console.log(b);

```

```bash
# 結果
5

1
```

</div>

---
layout: image-right
image: https://source.unsplash.com/collection/94734566/1920x1080
---

# 配列と連想配列
  
* ここではJavaScriptでよく使う配列と連想配列の考え方について学びます。

---

## 特徴と違いまとめ

データフォーマットであるJSONを構成する基本的な考え方になる為、  
それぞれの特徴をしっかり覚えておく必要がある。

|     |     |     |
| --- | --- | --- |
|<h2>配列</h2>| <kbd>[]</kbd>を使う、<u>位置番号</u>で取得 | <kbd>["dog", "apple"]</kbd>|
|<h2>連想配列</h2>| <kbd>{}</kbd>を使う、<u>Key名</u>を使って取得 |<kbd>{"animal" : "dog", "fruits": "apple"}</kbd>|

---
class: px-20
---

# 配列

宣言した変数に対して、pushメソッドで値の設定可能、位置番号で値を取得する。

<div grid="~ cols-2 gap-2" m="-t-2">

```ts {all|3-5}
let array = [];

array.push("dog");
array.push("cat");
array.push("monkey");

console.log(array);
console.log(array[0]);
```

```bash
# 結果
[ "dog", "cat", "monkey" ]

"dog"

```

</div>

---
class: px-20
---

# 連想配列

KeyとValue値で構成される、変数名とKeyを指定することで値の取得ができる。

<div grid="~ cols-2 gap-2" m="-t-2">

```ts {1,6-7,13-14|3-4|6-11}
let array = {};

// または
let array = new Object();

array.animal = "dog";
array.fruits = "apple"

// こちらでもOK
array["animal"] = "dog";
array["fruits"] = "apple";

console.log(array);
console.log(array.animal);
```

```js
// 結果
[object Object] {
  animal: "dog",
  fruits: "apple"
} 

"dog"

```

</div>

---
class: px-20
---

# 演習問題①

配列と連想配列を使って、consoleに下記の結果が出るようなデータを作ってください。

<div grid="~ cols-2 gap-2" m="-t-2">

```js
// まずはこちらを作成して表示

[object Object]{
  results: [
    {
      name: "kobayashi", 
      id: 1000, 
      tel: "080-1111-1111"
    },
    {
      name: "tanaka", 
      id: 2000, 
      tel: "080-2222-2222"
    },
    {
      name: "yamamoto", 
      id: 2000, 
      tel: "080-3333-3333"
    }
  ]
}

```

```js
// 左記のデータから以下を取得して表示

{
  name: "kobayashi", 
  id: 1000, 
  tel: "080-1111-1111"
}

"tanaka"

"080-3333-3333"

```

</div>

---
layout: statement
---

# EOF
