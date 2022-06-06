---
theme: default 
class: text-center
highlighter: prism 
lineNumbers: false
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
fonts:
  sans: Robot
title: Programming language workshop!
---
<div class="flex flex-col items-center justify-center h-full w-full"> 

<h1 class="font-extrabold text-transparent bg-clip-text bg-gradient-to-r from-purple-400 to-pink-600">
    Welcome to the workshop! 
</h1>

<img height="100" width="100" src="https://e.benjaminsmith.dev/hyperfastparrot">

</div>

<!-- ============================================================================================ -->
---
theme: default
class: text-center
title: Agenda
---
<div class="flex flex-col justify-center items-center h-full w-full">
<h2 class="font-extrabold text-transparent bg-clip-text bg-gradient-to-r from-purple-400 to-pink-600">
 Sooooo what exactly are we gonna do today?
</h2>
<br/>

**The basics of Interpreters**  
<span class="text-gray-400/50 flex flex-row items-center"> 
Lexers, AST, Pratt Parsing etc.
<img height="25" width="25" src="https://e.benjaminsmith.dev/yay">
</span>
 

**Making our own programming language** <br/>
<span class="text-gray-400/50 flex flex-row items-center">
Make a simple programming language with syntax similar to javascript
<img height="25" width="25" src="https://e.benjaminsmith.dev/sunglassesblob">
</span>

<div class="h-auto w-full items-center flex justify-center">
</div>
</div>

<!-- ============================================================================================ -->
---

<div  class="flex flex-col h-full w-full justify-center items-center">
<h1 class="font-extrabold text-transparent bg-clip-text bg-gradient-to-r from-purple-400 to-pink-600">
    What are `Interpreters`?
</h1>
<img height="60" width="60" src="https://e.benjaminsmith.dev/thonkage">
</div>

<!-- ============================================================================================ -->
---

<div class="flex flex-col items-center  w-full h-full">

<h1 class="font-extrabold text-transparent bg-clip-text bg-gradient-to-r from-purple-400 to-pink-600">
    Interpreters 
</h1>

An Interpreter is a computer program that directly executes instructions written in a programming or scripting language, without requiring them previously to have been compiled into a machine language program


```mermaid {scale: 0.5, theme: 'default'}
flowchart LR
    Program --> Lexer-- Tokens --> Parser-- AST --> Evaluator --> Result
```

</div>

<!-- ============================================================================================ -->
---

<h1 class="font-extrabold text-transparent bg-clip-text bg-gradient-to-r from-purple-400 to-pink-600">
    Lexer 
</h1>

Program  to  Tokens

Tokens are the "type of symbols" used in a program.

Program:
```js
let a = 3+7;
```

- special token: `let` 
- identifier: `a`
- symbol: `equals`
- integer literal: `3`
- symbol: `plus`
- integer literal: `7`
- symbol: `semicolon`

**Final tokenized result:** `let ident:a equals 3 plus 7 semicolon`

<!-- ============================================================================================ -->
---

<h1 class="font-extrabold text-transparent bg-clip-text bg-gradient-to-r from-purple-400 to-pink-600">
   Parser 
</h1>

Tokens to AST

AST stands Abstract Syntax Tree. It is basically a tree of tokens arranged in order of their operation.

`1 + 2 * 3`

Tokenized: `1 plus 2 asterisk 3`

```mermaid {theme: 'default', scale: 0.5}
stateDiagram-v2
    Add --> 1
    Add --> Mul
    Mul --> 2
    Mul --> 3
```
---

`let` statement AST: `let a = 3+20/5`

```mermaid {theme: 'default', scale: 0.5}
stateDiagram-v2
    let --> a
    let --> Add
    Add --> 3
    Add --> Div
    Div --> 20
    Div --> 5
```
<!-- ============================================================================================ -->
---

<h1 class="font-extrabold text-transparent bg-clip-text bg-gradient-to-r from-purple-400 to-pink-600">
   Evaluator 
</h1>

Loops around every node in the AST and evaluates it.

`let a = 3+20/5`

```mermaid {theme: 'default', scale: 0.3}
stateDiagram
    direction LR

    state "Division" as DivState {
        20 --> 4
        5 --> 4
    }

    state "Addition" as AddState {
        4 --> 7
        3 --> 7
    }

    state "Let Statement" as LetState {
        a
        7
    }
```

---

<div class="flex flex-col items-center justify-center h-full w-full"> 

<h1 class="font-extrabold text-transparent bg-clip-text bg-gradient-to-r from-purple-400 to-pink-600 flex flex-row">
    Let's start hacking!
    <!-- <img height="30" width="40" src="https://e.benjaminsmith.dev/cooll-thumbs"> -->
</h1>

<img height="100" width="100" src="https://e.benjaminsmith.dev/orpheus-pop">

</div>

