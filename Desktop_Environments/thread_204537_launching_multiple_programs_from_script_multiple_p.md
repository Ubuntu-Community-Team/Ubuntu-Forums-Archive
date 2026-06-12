---
title: "launching multiple programs from script multiple programs from script"
date: 2006-06-27
forum: Desktop Environments
---

### Post by cosmoshell on 2006-06-27
how can i make a script for the terminal  to run conky firefox dfm gaim firestarter etc without it stoping everytime it opens a program?

---

### Post by rai4shu2 on 2006-06-27
Did you try putting & at the end of each line?

---

### Post by cosmoshell on 2006-06-27
tried that and it only opened gaim

sudo firestarter &
dfm & 
gaim &
firefox &
conky &

---

### Post by thasheep on 2006-06-27
I think the sudo with the & could be causing problems because it expects input (your password) but other programmes are being run instead. Try putting firestarter last and without the & so that everything else is run first.```
dfm &
gaim &
firefox &
conky &
gksu firestarter
```(edit)changed sudo to gksu so that this script can be called from a panel menu entry or shortcut (doesn't need terminal input).

---

### Post by cosmoshell on 2006-06-27
now when i close the terminal. most of the programs close.

---

