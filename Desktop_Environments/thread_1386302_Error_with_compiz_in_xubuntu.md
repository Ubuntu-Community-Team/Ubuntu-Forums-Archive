---
title: "Error with compiz in xubuntu"
date: 2010-01-20
forum: Desktop Environments
---

### Post by kenichiaeb on 2010-01-20
Hi, I have a little problem with my xubuntu:
Today I installed xubuntu (It is extremely fast xD), and then I installed compiz and emerald to use the effects, but now the border of the windows changed to a style that I don't like, and when I try to change the theme, the border doesn't change, but everything else does, so what can I do to fix it?
Greetings

---

### Post by lidex on 2010-01-20
Emerald controls the window borders so you need to adjust that from emerald theme manager.

More info:
[http://wiki.compiz.org/]("http://wiki.compiz.org/")

Themes:
[http://compiz-themes.org/index.php?xcontentmode=103]("http://compiz-themes.org/index.php?xcontentmode=103")
[http://www.webupd8.org/2009/03/ubuntu-install-themes-emerald-compiz.html]("http://www.webupd8.org/2009/03/ubuntu-install-themes-emerald-compiz.html")

---

### Post by kenichiaeb on 2010-01-21
Yes, that's the problem, i can't modify the theme with emerald because when i apply the changes, the borders dissapears

---

### Post by lidex on 2010-01-21
Bring up a terminal and enter this command:
```
emerald --replace
```
Press the enter key.

---

