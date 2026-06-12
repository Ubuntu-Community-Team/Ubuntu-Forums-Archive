---
title: "system&gt; preferences&gt; keyboard shortcuts"
date: 2009-07-02
forum: Desktop Environments
---

### Post by macanudokiosko on 2009-07-02
Hi (first message of me)!

I wanted to know how to define a shortcut for opening a defined folder of my computer with a keyboard short cut:

   + add
      name: x folder
      command: ???

tx :)
macanudokiosko

---

### Post by asmoore82 on 2009-07-02
if you are using compiz, you will have to go through ccsm;
if you are using metacity, you can use `gconf-editor`

set a "custom command" keyboard shortcut and then
set that custom "run command" to something like:
```
nautilus */path/to/folder*
```

---

### Post by macanudokiosko on 2009-07-02
Good... that's made it.

many tx...

macanudokiosko :):KS

---

