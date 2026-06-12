---
title: "How to make only certain windows transparent in Berly"
date: 2007-06-09
forum: Desktop Effects &amp; Customization
---

### Post by HgBoy on 2007-06-09
I would like to have only a few of my windows (terminal, IDLE, etc) See-through, so i can type lines of code on them without switching pages constantly. What is the best way to accomplish this?

---

### Post by reclusivemonkey on 2007-06-10
Beryl Settings Manager;

Go to Window Management and then click on Set Window Attribs by various criteria. In Window Opacity, use

```
p:*program name*:*opacity value*
```

for example I have

```
p:cairo-clock:60
```

in mine.

---

