---
title: "launchpath and titlebar are disappeared (emergency)"
date: 2012-03-31
forum: Desktop Environments
---

### Post by woxuxow on 2012-03-31
launchpath and titlebar are disappeared and i can not switch between windows or maximize , close or minimize them
i wiped the gconf before occurrence

---

### Post by Frogs Hair on 2012-03-31
What Ubuntu version and desktop are you using ?

---

### Post by woxuxow on 2012-03-31
> **Frogs Hair said:**
> What Ubuntu version and desktop are you using ?

ubuntu 11.10 with unity (gnome 3.2.1) but i don`t know what version it is

---

### Post by Frogs Hair on 2012-03-31
If you can get into a terminal using Ctrl + Alt + T  try the following if you are using Unity .

```
unity --reset
```

---

### Post by woxuxow on 2012-04-01
> **Frogs Hair said:**
> If you can get into a terminal using Ctrl + Alt + T  try the following if you are using Unity .

```
unity --reset
```

thanks 
it temporary works but 
when i run it in terminal every thing goes well and every thing that was disappeared start to appear tile 

WARN  2012-04-01 11:04:26 unity.iconloader IconLoader.cpp:509 Unable to load contents of file:///usr/share/icons/unity-icon-theme/places/svg/category-available.svg: Error opening file: No such file or directory
^[^N
when i close terminal every changes get back
i installed unity-desktop but it changed nothing but unity-2d work well

---

### Post by Frogs Hair on 2012-04-01
You can try the following to reset Compiz as well as Unity.

```
Code:
gconftool-2 --recursive-unset /apps/compiz-1 

``` Then, open another terminal window, and run:```
unity --reset
```If you remain without a desktop and only with a Nautilus bar at the
top of the screen, go back to the first terminal window, and run the following.```
ccsm
```When the CCSM opens check the box with the Uity Plug-in . If all goes well Unity will return . Close the terminal even if you see a running process message .

---

### Post by woxuxow on 2012-04-02
Thanks dear
i removed the damaged account yesterday and created a new account it`s as fine as first day
thank you again

---

