---
title: "Searching Ubuntu"
date: 2006-02-24
forum: Desktop Environments
---

### Post by WelterPelter on 2006-02-24
So, coming from Mandrake (KDE), I'm used to searching with Konqueror, which has some fairly advanced features. The Gnome search tool is a little too basic for me, at least some of the time. What file search tool are most of you using all day?

---

### Post by bluevoodoo1 on 2006-02-24
```
locate blahblahblah
```

---

### Post by Trab on 2006-02-24
Beagle is similar to spotlight if thats wat u ment by search...

i know there is a howto somewhere for it, but as i cant find it... heres wat i know:
open a terminal
```
sudo apt-get install beagle 
```
it will probably need some other files too.... these  will install....
then
```
 beagle-settings 
```
set up your settings here....
you must now close your terminal...
now open a run prompt by using alt+F2
type
```
beagled
```
this is the beagle daemon, and is required to be running to use beagle.
it should auto start indexing...how long this takes depends on how much data u have, and wat u set it to search...
after it finishes searching, you can open beagle by typing 
```
best --no tray 
```
in a run prompt (Alt+F2) if u just want a search box, or 
```
 best 
``` if u want the Systray icon

hope that helps!

---

