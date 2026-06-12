---
title: "Icon size on Avant Window Navigator"
date: 2007-07-16
forum: Desktop Effects &amp; Customization
---

### Post by loopeando on 2007-07-16
I have a strange problem with my dock, the first icon is not at the same height than the others, see for yourselves:

[IMG]http://img390.imageshack.us/img390/8562/screenshotoy7.png[/IMG]

How can I fix this, because It's really bugging me out.

Thx in advance!

P.D: I have posted something similar on the AWN install thread but nobody gave it attention :(

---

### Post by chomafin on 2007-07-16
I don't believe there is a way to adjust single icons' in AWN.  You can adjust the total height within gconfig-editor....  I'd suggest trying the official Firefox Icon and see if it does the same thing.  The icon might have padding at the top of it in an alpha channel or somesutch.  

To adjust the total height/width/amount of rows : 
```
:~$ gconf-editor 
```
then browse to : /apps/avant-window-navigator/applets/1182476731/ (note, number may be different), and simply adjust the height

---

