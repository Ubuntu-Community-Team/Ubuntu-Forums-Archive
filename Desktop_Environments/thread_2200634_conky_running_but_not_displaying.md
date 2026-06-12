---
title: "conky running but not displaying"
date: 2014-01-20
forum: Desktop Environments
---

### Post by Lars Noodén on 2014-01-20
Conky runs for a while and then, seemingly randomly, will stop displaying.  Sending it a SIGHUP reloads the configuration file and causes it to resume displaying.  Sometimes it will display for a long time other times a short time but it seems it will always eventually stop displaying.  Has anyone seen this problem and know of a solution?

---

### Post by Lars Noodén on 2014-01-29
Still no closer to identifying the problem.  Even in debugging mode (-D) it provides no special output when it stops displaying.

---

### Post by Lars Noodén on 2014-05-05
For reference, it seems to be this bug:

[https://bugs.launchpad.net/ubuntu/+source/conky/+bug/1226277](https://bugs.launchpad.net/ubuntu/+source/conky/+bug/1226277)

---

### Post by grumblebum2 on 2014-05-05
In your conky config this setting usually causes this in unity.
```
own_window_type **desktop**
```

Try
```
own_window yes
own_window_transparent yes
own_window_type **override**
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
**#**own_window_argb_visual yes
own_window_argb_value 0
```
own_window_type **override** does not work well with argb transparency so comment that line out.
**override** windows are not under the control of the window manager. **own_window_hints** are ignored.

[SIZE=3]**or**[/SIZE]

```
own_window yes
own_window_transparent no
own_window_type **normal**
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_argb_visual yes
own_window_argb_value 100  #use 0-255 ... 0=0% opacity
```
own_window_type **normal** windows use **own_window_hints** and are under control of the window manager.
If own_window_transparent is set to **no** you can set a degree of transparency with **own_window_argb_visual yes**
and an **own_window_argb_value** between 0 and 255.
0=0% opacity
255=100% opacity
If own_window_transparent is set to **yes** and **own_window_argb_visual yes** is used 
the **own_window_argb_value** is ignored and the window is always fully transparent. 

When using own_window_type **normal**, compiz by default will minimize conky
with other windows when you show the desktop.
Use ccsm to untick **Hide Skip Taskbar Windows**
Logout or restart unity and conky to take effect.

---

### Post by Lars Noodén on 2014-05-07
The only one that had an effect was "own_window_type normal" and that put the output in a standard window available only on a single virtual desktop.  It's a step.

---

### Post by grumblebum2 on 2014-05-07
**own_window_type normal**
needs to be used with 
**own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager**

---

### Post by Lars Noodén on 2014-05-07
Thanks.  The two lines together fixed it.  

```
own_window_type normal
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

```

---

