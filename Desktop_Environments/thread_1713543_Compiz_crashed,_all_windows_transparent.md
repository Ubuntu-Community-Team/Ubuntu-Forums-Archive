---
title: "Compiz crashed, all windows transparent"
date: 2011-03-24
forum: Desktop Environments
---

### Post by Greth Rain on 2011-03-24
hey everyone, i'm really sorry if this is in the wrong section, i'm quite new here...

Problem:
I've been using ubuntu (Gnome) for about a year now...
and now i have a rather large (in my opinion) problem.
i have compiz-fusion install on my ubuntu and it has crashed.
i was setting the transparency for the title bars of windows (trying to).
suddenly compiz just crashed and now everything is transparent!:confused:
i can only see docky and the menu bar on top. all windows and menus are 100% transparent.
i am have a dual-boot with windows and am using it now. i also have ext2 reader installed, so i can access my files on ubuntu.

---

### Post by stinkeye on 2011-03-24
2 ways.The first way you'll be running blind but should work
 
Boot into ubuntu and once loaded

[SIZE="2"]**1...**[/SIZE]
Hit alt+F2
Type ```
metacity --replace
```
and hit the Enter key.
Go to **[SIZE="2"]3[/SIZE]**

[SIZE="2"]**2...**[/SIZE] 
hit ctrl+alt+F1
logon
Run...
```
DISPLAY=":0.0" metacity --replace &
```
Hit ctrl+c
run..
```
logout
```

Hit ctrl+alt+F7 (sometimes I have to use ctrl+alt+F8 ) 


[SIZE="2"]**3...**[/SIZE]
You should now be running metacity as your window manager.
Fix up  your compiz settings.
If your unsure which compiz setting you have changed you can reset 
all your compiz settings back to default with..
```
gconftool-2 --recursive-unset /apps/compiz
```


Run...
```
compiz --replace &
```
and you'll be back in compiz.

---

### Post by Greth Rain on 2011-03-24
Thx stinkeye, will try it out asap.;)

---

### Post by stinkeye on 2011-03-24
You may also be able to make the windows appear by hovering over where you
think they are, with the mouse and hold down alt while scrolling up with the mouse wheel.

---

