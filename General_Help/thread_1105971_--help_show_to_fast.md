---
title: "--help show to fast"
date: 2009-03-25
forum: General Help
---

### Post by cazz on 2009-03-25
hi, this maybe sound to basic but when I run fpr example

program --help

then the help show everything but I have not so big screen so I miss alot at the beginning.

is that anyway I scan scroll or pause so I can read from begin?

---

### Post by eldragon on 2009-03-25
if you are doing it in the run dialog, its an expected feature..

you should find the gnome-terminal and run those in there.

its under apps. accesories

---

### Post by issih on 2009-03-25
Yes, certainly, on a gnome terminal or any modern terminal emulator you can just scroll up with the scroll bars at the side of the window.

Alternatively if you are using a very low level terminal you can pipe the output into something like 'more' or 'less' which will then give you the ability to work through the text bit at a time.

e.g.

```
firefox --help | more
```

hope that helps

---

### Post by cazz on 2009-03-25
Thanks alot :)

---

