---
title: "Conky Wallpaper Embedded Terminal"
date: 2009-06-15
forum: Desktop Environments
---

### Post by SilverSnakeEyes on 2009-06-15
[SIZE=2][COLOR=#204A87]** **[/COLOR][/SIZE][SIZE=2]I'm trying to embed the terminal in my wallpaper using compiz.
[COLOR=#204A87]****[/COLOR][/SIZE][SIZE=2]I'm having no problems, except for one thing. When I try to change decoration windows to affect both the instance of the terminal, and "any" it does not work. I've tried ```
any & (title=embeddedterminal)
```[/SIZE][SIZE=2] and ```
any !title=embeddedterminal
```.

My goal is for all windows and the embedded terminal to be affected by windows decorations. title=embeddedterminal gives me a transparent embedded terminal, but takes away the minimize maximize and close buttons. any makes the would be transparent terminal have its own window. (Which is what I don't want).
[/SIZE]

---

### Post by loomsen on 2009-06-15
(any) & !(title=embeddedterminal)

---

### Post by SilverSnakeEyes on 2009-06-15
Doesn't work for me, the terminal still has a window and is mini/maxi mizable.

---

### Post by SilverSnakeEyes on 2009-06-15
Nevermind, solved the problem, had to change the profile of the terminal so that it stayed embeddedterminal as the title after loading.

---

