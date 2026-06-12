---
title: "lost the frame around my windows"
date: 2008-12-14
forum: General Help
---

### Post by stupor on 2008-12-14
lost the frame around my windows only when im on the net.

---

### Post by Izek on 2008-12-14
So basically, you lose your window decoration when firefox opens?

---

### Post by blazemore on 2008-12-14
Have you got a screenshot?
Are you sure it's not just Firefox off the top of the screen?

Try holding alt, and clicking and dragging the window down.

Otherwise, try alt+F2, and then enter
```
metacity --replace
```

If that doesn't work, do you usre compiz?
If you do, try alt+F2
```
sudo apt-get install fusion-icon emerald -y
```
and check "Run in terminal"

Then alt+F2
```
fusion-icon
```
and right-click the new icon that appears in the notification area, select window maneger->GTK window decorator

Then do System->Preferences->Sessions, and add Fusion-icon as a startup entry

---

### Post by stupor on 2008-12-15
thank you metacity --replace fixed the problem

---

### Post by blazemore on 2008-12-15
Well if you ever use Compiz you'll have to use the second fix.

---

### Post by mosestruong on 2009-02-03
I'm having this problem but only with Firefox using Compiz windows manager. Does anyone know a fix for this? Installing Emerald and Fusion-icon didn't help. Thanks

---

### Post by eotakos on 2009-02-03
does anyone know why the "thanks" feature is disabled throughout the forum?

... cause i'd like to thank blazemore for the usefull "alt + f2" and the "metacity --replace"  tips!


i have a kind of graphical setback with openoffice myself. this happened when i uninstalled the repos. version in order to replace it with the one from the website. since then of course, i realized it was no use and changed back to the repos versions but the problem remained... 

if you notice the screen-shot you'll see that  the scroll bars are "out of theme" , as well as the  menu toolbar... any suggestions?

---

