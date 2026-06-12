---
title: "Making my functionbuttons work properly"
date: 2011-07-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by senca on 2011-07-04
Hey guys,
I can't find a good solution for this one. I'm working on  a Dell XPS with Ubuntu 10.10.
For some reason my function buttons only work for the actual functions. With this I mean that for example pressing fn+F5 raises the screen brightness but pressing F5 without fn does that to. So I lost all my F buttons (for example when executing a query in PGadmin, F5 is the execute button) which is very annoying since I need to use them quite often.
Also F4 lowers my screen brightness only 1 unit but stops then.
Does any one what plugins or so would be helpfull to fix this?

greets

---

### Post by senca on 2011-08-02
Bump!

Still very annoying but no answer :)
Fingers crossed!

edit: I just messed with fn and a lot of other buttins and seem to have switched the F buttons and the symbols on it. When using fn it works with the F buttons and without fn I can use the symbols. That the other way around but this works. Now if anyone can tell me how to turn it around. :p

---

### Post by senca on 2011-08-08
Is this the hardest question ever asked?:)

---

### Post by Skadork on 2011-08-10
some keyboards have a function lock button.  check yours to see if it has one...

---

### Post by anieruddha on 2011-08-10
There is some setting in bios, to use F keys as regular function keys and those increase/decrease brightness will work only if u use Fn+F keys.

It works for me. I m using DEll Inspiron.

---

### Post by Basher101 on 2011-08-10
You can change your brightness completely with a command```
sudo setpci -s 00:02.0 F4.B=0
```the brightness is in HEX. 0 is brightest possible, while FF is darkest possible (e.g. backlight turns off). Just try double letters such as aa , bb or cc , that will make your brightness jump a few levels.

---

