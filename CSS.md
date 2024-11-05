# CSS

基础不牢，地动山摇，来复习一下CSS为tailwind打基础。

##  CSS 基础语法和选择器

### 基础语法

CSS（Cascading Style Sheets，层叠样式表）是一种用于描述HTML文档样式的样式表语言，以下是CSS基础语法的详细介绍：

#### CSS规则结构

一个CSS规则主要由两部分构成：**选择器** 和 **声明块**。

- **选择器**：指定需要添加样式的HTML元素。例如，`p` 表示选中所有的 `<p>` 元素。
- **声明块**：包含一条或多条声明，每条声明由一个属性和一个值组成，并用冒号分隔。声明块用大括号 `{}` 括起来。

```css
p {
  color: red;
  text-align: center;
}
```

####  CSS注释

CSS注释用于解释代码，不会被浏览器解析。注释以 `/*` 开始，以 `*/` 结束。

```css
/* 这是一个注释 */
p {
  text-align: center;
}
```

#### 应用CSS到HTML

要将CSS样式应用到HTML文档中，通常有以下几种方法：

- **内联样式**：直接在HTML元素中使用 `style` 属性定义样式。
- **内部样式表**：在HTML文档的 `<head>` 部分使用 `<style>` 标签定义样式。
- **外部样式表**：创建一个单独的CSS文件（例如 `style.css`），然后在HTML文档的 `<head>` 部分通过 `<link>` 标签引入该文件。

### 选择器

#### 通配符选择器（Universal Selector）

通配符选择器（`*`）会选择文档中的所有元素。它通常用于重置所有元素的默认样式。

```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
```

#### 元素选择器（Type Selector）

元素选择器通过元素名称来选择HTML文档中的所有相应元素。例如，`p` 选择所有的 `<p>` 元素。

```css
p {
  color: blue;
}
```

#### 类选择器（Class Selector）

类选择器通过类名来选择元素。在HTML中，类名通过 `class` 属性添加到元素上，而在CSS中，类选择器以一个点（`.`）开头。

```css
/* 选择所有class为"highlight"的元素 */
.highlight {
  background-color: yellow;
}
```

#### ID选择器（ID Selector）

ID选择器通过元素的ID来选择特定的元素。在HTML中，ID通过 `id` 属性添加到元素上，而在CSS中，ID选择器以一个井号（`#`）开头。每个ID在页面中应该是唯一的。

```css
/* 选择id为"main-content"的元素 */
#main-content {
  font-size: 16px;
}
```

#### 属性选择器（Attribute Selector）

属性选择器可以根据元素的属性及其值来选择元素。它们以方括号（`[]`）表示。

```css
/* 选择所有具有href属性的<a>元素 */
a[href] {
  color: green;
}

/* 选择所有href属性值以"https"开头的<a>元素 */
a[href^="https"] {
  background-image: url('lock.png');
}

/* 选择所有title属性值包含"flower"的元素 */
[title*="flower"] {
  border: 1px solid #000;
}
```

### 组合选择器

####  分组选择器（Grouping Selector）

分组选择器允许你将多个选择器放在一个规则集中，这样你可以为多个选择器定义相同的样式。

```css
h1, h2, h3 {
  font-family: 'Arial', sans-serif;
}
```

#### 子选择器（Child Selector）

子选择器（`>`）用于选择指定元素的直接子元素。

```css
li > a {
  color: red;
}
```

#### 后代选择器（Descendant Selector）

后代选择器用于选择指定元素的所有后代元素，无论它们在DOM树中的深度如何。

```css
ul li a {
  text-decoration: none;
}
```

#### 相邻兄弟选择器（Adjacent Sibling Selector）

相邻兄弟选择器（`+`）选择紧接在另一个元素后的元素，且两者有相同的父元素。

```css
h2 + p {
  margin-top: 0;
}
```

#### 通用兄弟选择器（General Sibling Selector）

通用兄弟选择器（`~`）选择指定元素之后的所有符合条件的兄弟元素。

```css
h2 ~ p {
  font-style: italic;
}
```

### 伪类和伪元素选择器

伪类和伪元素是CSS选择器的特殊类型，它们允许你根据特定状态或信息来应用样式，而不需要添加额外的类或结构。

#### 伪类选择器（Pseudo-class Selector）

伪类用于选择处于特定状态的元素。它们以冒号（`:`）开头。

```css
/* 选择所有未访问的链接 */
a:link {
  color: purple;
}

/* 选择所有访问过的链接 */
a:visited {
  color: purple;
}

/* 选择鼠标悬停时的元素 */
a:hover {
  text-decoration: underline;
}
/* 选择鼠标按下时的元素 */
a:active {
  background-color: #ccc;
}

/* 选择获得焦点的<input>元素 */
input:focus {
  outline: 2px solid blue;
}
```

`:first-child` 伪类用于匹配其父元素的第一个子元素，而 `:last-child` 用于匹配最后一个子元素；`:nth-child(n)` 伪类匹配其父元素的第n个子元素。

```css
li:first-child {
  font-weight: bold;
}

li:last-child {
  font-style: italic;
}

li:nth-child(2) {
  color: green;
}
```



#### 伪元素选择器（Pseudo-element Selector）

伪元素用于选择和操作文档中的特定部分，如元素的首字母、首行等。它们以双冒号（`::`）开头。

```css
/* 选择每个<p>元素的首行 */
p::first-line {
  font-weight: bold;
}

/* 选择每个<p>元素的首字母 */
p::first-letter {
  font-size: 200%;
}
```

 `::before` 和 `::after`这两个伪元素用于在指定元素的内容之前或之后插入生成的内容。

```css
h1::before {
  content: "Chapter ";
}

h1::after {
  content: " - End";
}
```

`::selection` 伪元素用于匹配用户选择的文本部分。

```css
::selection {
  background-color: yellow;
  color: black;
}
```

在使用伪元素时，注意旧版浏览器可能需要使用单冒号语法（如 `:before`），但现代浏览器推荐使用双冒号（如 `::before`）来区分伪类和伪元素。

### 层叠规则与优先级

CSS层叠规则和优先级确保了样式能够以一致和可预测的方式应用于网页元素，了解这些规则有助于解决样式冲突，确保网页的视觉效果符合设计意图。通过掌握这些原则，开发者可以更有效地编写和维护CSS代码

#### 层叠规则（Cascading）

CSS层叠规则是指在HTML文档中，当多个样式声明试图应用于同一个元素时，浏览器如何决定使用哪个样式。

1. **来源**：

   样式来源的优先级顺序由高到低：

   - 行内样式（在`style`属性上定义的样式）

   - 内联样式（在`style`标签中定义的样式）

   - 外部样式表

2. **优先级**：

   优先级是根据选择器的类型和数量来计算的。优先级高的样式将覆盖优先级低的样式。

3. **重要性**：

   `!important` 声明的样式总是优先于其他样式，除非有另一个同样带有 `!important` 的样式声明具有更高的优先级。

4. **顺序**：

   如果优先级和来源都相同，那么样式表中后来定义的样式将覆盖之前定义的样式。

#### 理解优先级

CSS中的优先级是通过特定的规则来决定的

1. **选择器类型**：不同类型的选择器具有不同的权重。例如，ID选择器的权重高于类选择器，内联样式具有最高的权重。
2. **权重计算**：权重可以通过一个四元组 `a, b, c, d` 来表示，其中：
   - `a` 表示 `!important` 的数量。
   - `b` 表示ID选择器的数量。
   - `c` 表示类选择器、属性选择器和伪类的数量。
   - `d` 表示元素选择器和伪元素的数量。
3. **冲突解决**：当多个规则冲突时，权重高的规则会覆盖权重低的规则。如果权重相同，则后面的规则会覆盖前面的规则。

#### 举例说明

内联样式 (`style="color: purple;"`) 的优先级高于所有的外部和内部 CSS 选择器，因此这里会显示为紫色。

```html
<div id="special" class="text" style="color: purple;">这是一个测试文本</div>
```



## 盒模型（Box Model）

### 基本组成

CSS的盒模型（Box Model）是理解页面布局的基础。每个HTML元素都可以看作是一个矩形的盒子，这个盒子由以下四个部分组成：

#### 内容（Content）

内容区域是盒子的中心，它包含元素的实际内容，比如文本、图片等。

- `width`：设置元素的宽度。
- `height`：设置元素的高度。

```css
.element {
  width: 200px;  /* 内容宽度为200像素 */
  height: 150px; /* 内容高度为150像素 */
}
```

#### 内边距（Padding）

内边距位于内容周围，它是指内容与盒子边缘之间的空间。

- `padding`：可以设置上、右、下、左四个方向的内边距。
- `padding-top`：设置元素的上内边距。
- `padding-right`：设置元素的右内边距。
- `padding-bottom`：设置元素的下内边距。
- `padding-left`：设置元素的左内边距。

```css
.element {
  padding: 10px;        /* 四边内边距均为10像素 */
  padding: 10px 5px;    /* 上下内边距为10像素，左右内边距为5像素 */
  padding: 10px 5px 15px; /* 上内边距为10像素，左右内边距为5像素，下内边距为15像素 */
  padding: 10px 5px 15px 20px; /* 上内边距为10像素，右内边距为5像素，下内边距为15像素，左内边距为20像素 */
  padding-top: 10px;    /* 只设置上内边距为10像素 */
  /* 可以单独设置其他三个方向的padding */
}
```

#### 边框（Border）

边框位于内边距的外围，它包围着内容和内边距。

- `border`：可以设置边框的宽度、样式和颜色。
- `border-width`：设置边框的宽度。
- `border-style`：设置边框的样式（如`solid`, `dashed`, `dotted`等）。
- `border-color`：设置边框的颜色。
- 单边设置：`border-top`, `border-right`, `border-bottom`, `border-left`。

```css
.element {
  border: 1px solid black; /* 设置边框宽度为1像素，样式为实线，颜色为黑色 */
  border-width: 2px;       /* 设置边框宽度为2像素 */
  border-style: dashed;    /* 设置边框样式为虚线 */
  border-color: red;       /* 设置边框颜色为红色 */
  border-top: 1px solid blue; /* 只设置上边框宽度为1像素，样式为实线，颜色为蓝色 */
  /* 可以单独设置其他三个方向的边框 */
}
```

#### 外边距（Margin）

外边距位于边框的外围，它是盒子与其他元素之间的空间。

- `margin`：可以设置上、右、下、左四个方向的外边距。
- `margin-top`：设置元素的上外边距。
- `margin-right`：设置元素的右外边距。
- `margin-bottom`：设置元素的下外边距。
- `margin-left`：设置元素的左外边距。

```css
.element {
  margin: 10px;        /* 四边外边距均为10像素 */
  margin: 10px 5px;    /* 上下外边距为10像素，左右外边距为5像素 */
  margin: 10px 5px 15px; /* 上外边距为10像素，左右外边距为5像素，下外边距为15像素 */
  margin: 10px 5px 15px 20px; /* 上外边距为10像素，右外边距为5像素，下外边距为15像素，左外边距为20像素 */
  margin-top: 10px;    /* 只设置上外边距为10像素 */
  /* 可以单独设置其他三个方向的外边距 */
}
```

### 盒模型类型

在CSS中，有两种盒模型：

1. **标准盒模型（W3C盒模型）**：在标准盒模型中，元素的`width`和`height`属性只包含内容（Content）的宽度和高度。内边距（Padding）、边框（Border）和外边距（Margin）都在这个基础上添加。
2. **IE盒模型（替代盒模型）**：在IE盒模型中，元素的`width`和`height`属性包含内容（Content）、内边距（Padding）和边框（Border）的宽度。只有外边距（Margin）是额外的。

可以通过`box-sizing`属性来切换盒模型。将`box-sizing`设置为`border-box`，可以让元素的宽度和高度包含内边距和边框，类似于IE盒模型。

```css
.box {
  box-sizing: border-box; /* 使用IE盒模型 */
}
```

### 外边距合并现象

在CSS中，相邻元素之间的`margin`合并问题是一个常见的布局现象。当两个垂直排列的块级元素（例如两个`div`）都有垂直方向的外边距（`margin`）时，它们之间的外边距不会简单地相加，而是会合并为一个外边距，这个合并后的外边距等于两个外边距中的较大者。

**如何防止margin合并？**

- **使用border或padding**：在元素之间添加`border`或者`padding`可以阻止外边距合并。
- **创建BFC（块级格式化上下文）**：例如，设置元素的`overflow`属性为非`visible`值（如`hidden`、`scroll`或`auto`）可以创建一个新的BFC，从而防止外边距合并。
- **浮动元素**：浮动元素不会与其他元素发生外边距合并。
- **绝对定位元素**：绝对定位的元素也不会与其他元素发生外边距合并。

## 文本和字体样式

### 字体样式

1. `font-family`

   定义文本使用的字体名称。可以指定多个字体名称作为备选，以防首选字体不可用。
   
   ```css
   font-family: '字体名称', '备选字体1名称', '备选字体2名称';
   ```

2. `font-size`

   设置文本的大小。可以采用多种单位，如像素(px)、em、rem、百分比(%)等。

   ```css
   font-size: 16px; /* 像素单位 */
   font-size: 1em; /* 相对于父元素的字体大小 */
   font-size: 100%; /* 相对于父元素的字体大小 */
   ```

3. `font-style`

   定义文本的样式，如正常、斜体等。

   ```css
font-style: normal; /* 正常文本 */
font-style: italic; /* 斜体文本 */
font-style: oblique; /* 倾斜文本 */

   ```

4. `font-weight`

   设置文本的粗细程度。

   ```css
font-weight: normal; /* 相当于400 */
font-weight: bold; /* 相当于700 */
font-weight: 100; /* 100-900的数值，100最细，900最粗 */
   ```

5. `line-height`

   设置行间的距离，可以影响文本的垂直间距。

   ```css
line-height: 1.5; /* 无单位数值，相对于字体大小 */
line-height: 24px; /* 像素单位 */
line-height: 150%; /* 百分比单位 */
   ```

6. `font`

   这是一个简写属性，用于同时设置多个字体属性。

   ```css
   font: italic bold 16px/1.5 '字体名称','备选字体';
   
   /* 等价于 */
   font-style: italic;
   font-weight: bold;
   font-size: 16px;
   line-height: 1.5;
   font-family: '字体名称','备选字体';
   ```

7. `@font-face`

   这是一个规则，允许网页下载并使用自定义字体。

   ```css
   @font-face {
    font-family: 'MyCustomFont';
    src: url('mycustomfont.woff2') format('woff2'),
       url('mycustomfont.woff') format('woff');
    font-weight: normal;
    font-style: normal;
   }
   ```

### 文本样式

1. `text-align` 

   用于设置文本的水平对齐方式。

   ```css
   text-align: left;  /*左对齐文本*/
   text-align: right;  /*右对齐文本*/
   text-align: center;  /*居中对齐文本*/
   ```

2. `vertical-align` 

   用于设置元素的垂直对齐方式。

   ```css
   vertical-align: baseline; /* 基线对齐 */
   vertical-align: bottom; /* 底端对齐 */
   vertical-align: middle; /* 中部对齐 */
   ```

3. `text-indent` 

   用于指定文本的第一行缩进的大小。

   ```css
   text-indent: 20px; /* 使用像素值设置缩进 */
   text-indent: 10%; /* 使用百分比设置缩进 */
   ```

4. `text-decoration` 

   用于设置文本的装饰线，比如下划线、上划线、删除线等。

   ```css
   text-decoration: none; /* 没有装饰线 */
   text-decoration: underline; /* 下划线 */
   text-decoration: overline; /* 上划线 */
   text-decoration: line-through; /* 删除线 */
   ```

5. `text-transform` 

   用于控制文本的大小写。

   ```css
   text-transform: none; /* 不改变文本的大小写 */
   text-transform: capitalize; /* 将每个单词的首字母大写 */
   text-transform: uppercase; /* 将所有字符转换为大写 */
   text-transform: lowercase; /* 将所有字符转换为小写 */
   ```

### 颜色和背景

1. `color` 用于设置文本的颜色。

   ```css
   color: red; /* 设置段落文本颜色为红色 */
   color: #ff0000; /* 使用十六进制颜色代码设置文本颜色 */
   color: rgb(255, 0, 0); /* 使用RGB值设置文本颜色 */
   color: rgba(255, 0, 0, 0.5); /* 使用RGBA值设置文本颜色，包括透明度 */
   color: hsl(0, 100%, 50%); /* 使用HSL值设置文本颜色 */
   color: hsla(0, 100%, 50%, 0.5); /* 使用HSLA值设置文本颜色，包括透明度 */
   ```

1. `background-color` 属性用于设置元素的背景颜色。

   ```css
   background-color: blue; /* 设置背景颜色为蓝色 */
   background-color: #0000ff; /* 使用十六进制颜色代码设置背景颜色 */
   ```

2. `background-image` 属性用于设置元素的背景图像。

   ```css
   background-image: url('image.jpg'); /* 设置背景图像为图片文件 */
   background-image: linear-gradient(red, yellow); /* 从红色到黄色的线性渐变 */
   background-image: radial-gradient(circle, red, yellow, green); /* 从红色到黄色再到绿色的径向渐变 */
   ```

3. `background-position` 属性用于设置背景图像的位置。

   ```css
   background-image: url('image.jpg');
   background-position: top left; /* 背景图像位于元素的左上角 */
   background-position: 50% 50%; /* 背景图像位于元素的中央 */
   ```

4. `background-size` 属性用于设置背景图像的尺寸。

   ```css
   background-image: url('image.jpg');
   background-size: cover; /* 背景图像覆盖整个元素，可能会裁剪部分图像 */
   background-size: contain; /* 背景图像完整地适应元素，可能会有空白区域 */
   background-size: 50% 25%; /* 设置背景图像的宽度和高度为元素宽高的百分比 */
   ```

5. `background-repeat` 属性用于控制背景图像的重复方式

   ```css
   background-image: url('pattern.png');
   background-repeat: repeat; /* 默认值，背景图像在水平和垂直方向上重复 */
   background-repeat: no-repeat; /* 背景图像不重复 */
   background-repeat: repeat-x; /* 背景图像仅在水平方向上重复 */
   background-repeat: repeat-y; /* 背景图像仅在垂直方向上重复 */
   ```

6. `background-attachment` 属性用于控制背景图像是否随页面滚动。

   ```css
   background-image: url('image.jpg');
   background-attachment: scroll; /* 默认值，背景图像随页面滚动 */
   background-attachment: fixed; /* 背景图像固定，不随页面滚动 */
   background-attachment: local; /* 背景图像随元素内容滚动 */
   ```

7. `background` 是一个简写属性，用于一次性设置所有背景相关的属性。

   ```css
   background: #ffffff url('image.jpg') no-repeat right top; /* 设置背景颜色、图像、重复和位置 */
   ```

8. `opacity` 属性用于设置元素的透明度，影响元素以及其所有子元素的透明度。

   ```css
   opacity: 0.5; /* 设置元素及其子元素的透明度为50% */
   ```

9. `box-shadow` 属性用于在元素的框上添加阴影效果。

   ```css
   box-shadow: 10px 10px 5px 0px rgba(0,0,0,0.75); /* 水平阴影位置、垂直阴影位置、模糊距离、阴影扩展距离和颜色 */
   ```

   

### 4. 布局基础

- **display 属性**：`block`、`inline`、`inline-block`、`none` 的区别。
- **浮动（float）与清除浮动**：浮动布局的原理，使用 `clear` 清除浮动的多种方法（如 clearfix）。
- **定位（position）**：静态（`static`）、相对（`relative`）、绝对（`absolute`）、固定（`fixed`）和粘性（`sticky`）定位。
- **层级（z-index）**：层级控制及其影响因素。

### 5. Flexbox 布局

- **容器属性**：`display: flex`、`flex-direction`、`justify-content`、`align-items`、`flex-wrap` 等。
- **项目属性**：`flex-grow`、`flex-shrink`、`flex-basis`、`align-self`。
- **常见布局模式**：水平、垂直居中，网格布局，响应式卡片布局。

### 6. CSS Grid 布局

- **定义网格容器**：`display: grid`、`grid-template-columns`、`grid-template-rows`。
- **定义网格项目**：`grid-column`、`grid-row`，`grid-area` 等。
- **对齐和间距**：`gap`、`justify-items`、`align-items`、`place-items`。
- **模板布局**：`grid-template-areas` 创建更复杂的布局。

### 7. 响应式设计与媒体查询

- **基础概念**：移动优先 vs. 桌面优先，媒体查询的编写方式。
- **媒体查询**：`@media` 的用法，常用断点（如 `min-width`、`max-width`）。
- **响应式单位**：百分比、`em`、`rem`、`vw`、`vh`，及它们在不同场景的应用。

### 8. 动画与过渡效果

- **过渡效果**：`transition` 属性，`transition-property`、`transition-duration`、`transition-timing-function`。
- **动画**：`@keyframes` 定义，`animation` 属性，`animation-delay`、`animation-iteration-count` 等。
- **应用场景**：按钮的悬停效果、加载动画、渐入渐出效果。

### 9. CSS 变量和自定义属性

- **定义和使用**：`--变量名: 值;` 和 `var(--变量名)`。
- **优点**：复用性、主题切换和动态更新样式。

### 10. CSS 框架的基本用法（如 Tailwind、Bootstrap 等）

- **实用工具类**：快速构建常见的 UI 元素。
- **优势与限制**：在使用框架时，理解其限制和定制方法。

### 11. 浏览器兼容性与调试

- **兼容性工具**：使用开发者工具检查兼容性，兼容性写法。
- **调试方法**：使用浏览器开发者工具检查元素样式、调试布局问题、分析动画性能。