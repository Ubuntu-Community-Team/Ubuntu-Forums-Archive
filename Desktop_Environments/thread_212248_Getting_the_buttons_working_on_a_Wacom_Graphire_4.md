---
title: "Getting the buttons working on a Wacom Graphire 4"
date: 2006-07-09
forum: Desktop Environments
---

### Post by stoffe on 2006-07-09
I remember there was some discussion about this during Dapper development with no solutions, but now I've found one: [http://foto-cs.de/blog/item/196](http://foto-cs.de/blog/item/196)

Based on expresskeys, works just fine as per instructions. :)

I modified the config somewhat, inverting the scrolling and adding ALT-left and ALT-right to the buttons for browsing for now...
```
00 Program Name:                        "default"       # Name must be within double quotes ""
01 Scroll Wheel Up:             995
02 Scroll Wheel Up Plus:        0
03 Scroll Wheel Down:           994
04 Scroll Wheel Down Plus:      0
05 Left Button:                 64
06 Left Button Plus:            100
07 Right Button:                64
08 Right Button Plus:           102
```

Hope that helps someone else!

---

### Post by twisted_steel on 2006-07-25
Wow, just what I was looking for.  The config you posted works quite well for web browsing :D

---

