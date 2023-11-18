# <p align="center">🟢🟡🔴 Jello 🔴🟡🟢</p>

<p align="center">
    <a href="https://github.com/codereport/array-language-comparisons/issues" alt="contributions welcome">
        <img src="https://img.shields.io/badge/contributions-welcome-brightgreen.svg?style=flat" /></a>
    <a href="https://lbesson.mit-license.org/" alt="MIT license">
        <img src="https://img.shields.io/badge/License-MIT-blue.svg" /></a>
    <a href="https://www.python.org/">
        <img src="https://img.shields.io/badge/Python-3-ff69b4.svg"/></a>
    <a href="https://github.com/codereport?tab=followers" alt="GitHub followers">
        <img src="https://img.shields.io/github/followers/codereport.svg?style=social&label=Follow" /></a>
    <a href="https://GitHub.com/codereport/jello/stargazers/" alt="GitHub stars">
        <img src="https://img.shields.io/github/stars/codereport/jello.svg?style=social&label=Star" /></a>
    <a href="https://twitter.com/code_report" alt="Twitter">
        <img src="https://img.shields.io/twitter/follow/code_report.svg?style=social&label=@code_report" /></a>
</p>

### Description

A Python script for wrapping the Jelly executable so you can more easily play with the language.

### Links

* [Jelly GitHub Repo](https://github.com/DennisMitchell/jellylanguage/)
* [Jelly Online Interpreter](https://jellyballs.github.io/)

### Chain Patterns

#### Special Chain Names

* **LCC:** [Leading Constant Chain](https://github.com/DennisMitchell/jellylanguage/wiki/Tutorial#whats-the-starting-value)
* **LDC:** Leading Dyadic Chain (described in the first buller **here**)
* **JL:** Just use Left Arg (as `v`)

#### Monadic Chains

**Q: What makes my chain monadic?**
A: If you only pass it one argument (aka `ω`)

|       | Chain pattern | New `v` value | Chain Type |     Name     | CinM¹ |
| :---: | :-----------: | :-----------: | :--------: | :----------: | :---: |
|   1   |   `+ F ...`   |   `v+F(ω)`    |   `2-1`    | `dyad-monad` |   S   |
|   2   |   `+ 1 ...`   |     `v+1`     |   `2-0`    | `dyad–nilad` |       |
|   3   |   `1 + ...`   |     `1+v`     |   `0-2`    | `nilad-dyad` |       |
|   4   |    `+ ...`    |     `v+ω`     |    `2`     |              |   -   |
|   5   |    `F ...`    |    `F(v)`     |    `1`     |              |   -   |

* ¹ Combinator in Monadic Case
* ² Combinator in Dyadic Case

#### Dyadic Chains

**Q: What makes my chain dyadic?**
A: If you pass it two arguments (aka `λ` and `ρ`)

|       | Chain pattern | New `v` value | Chain Type |       Name        | CinD² |
| :---: | :-----------: | :-----------: | :--------: | :---------------: | :---: |
|   1   |  `+ × 1 ...`  |  `(v+ρ)×1`*   |  `2-2-0`   | `dyad-dyad-nilad` |   E   |
|   2   |   `+ × ...`   |   `v+(λ×ρ)`   |   `2-2`    |    `dyad-dyad`    |   ε   |
|   3   |   `+ 1 ...`   |     `v+1`     |   `2-0`    |   `dyad-nilad`    |       |
|   4   |   `1 + ...`   |     `1+v`     |   `0-2`    |   `nilad-dyad`    |       |
|   5   |    `+ ...`    |     `v+ρ`     |    `2`     |
|   6   |    `F ...`    |    `F(v)`     |    `1`     |

### Combinator Table (WIP)

| Combinator | Chain Spelling |
| :--------: | :------------: |
|     S      | `2-1` monadic  |
|     B₁     |  `2-1` dyadic  |
|     E      |
|     ε      |

### Examples

#### Example 1 (from [Section 1](https://github.com/DennisMitchell/jellylanguage/wiki/Tutorial#1tacit-programming))

`+H` can be called monadically or dyadically, and is a `2-1` chain.
* If called monadically, its a `2-1` monadic train, aka the `S` combinator.
* If called dyadically, it is a `JL`+`5`+`6`, which ends up being the `B₁` combinator.

#### Example 2 (from [Section 4.2](https://github.com/DennisMitchell/jellylanguage/wiki/Tutorial#42monadic-chains))

`+²×` can be called **monadically** or dyadically, and it is a `2-1-2` chain.
* If called monadically, `S` forms a monadic function, that is then used in `Σ`
* If called dyadically, the `2-1` is the `B₁` combinator, and then used in a `Φ₁` where the left dyadic function is `⊢`.

#### Example 3 (from [Section 4.3](https://github.com/DennisMitchell/jellylanguage/wiki/Tutorial#43dyadic-chains))

`+×÷H` can be called monadically and **dyadically**, and it is a `2-2-2-1` chain.
* If called monadically, apply `W` is applied, then evalaate the `2-2` part as repeated (or 2) `S` combinators, and then the `2-1` chain at the end matches the `S` combinator.
* If called dyadically, we have a LDC, which means the `2-2-2` forms the `Φ₁` which yield a binary function that is then used in the sits inside a `B₁` along with the final monadic operation.
