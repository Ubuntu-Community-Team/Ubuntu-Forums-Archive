---
title: "Weird graphics problem on WoW"
date: 2007-08-11
forum: Gaming &amp; Leisure
---

### Post by GvsE on 2007-08-11
I have this weird problem while i play world of warcraft on my ubuntu 7.04. 

Here's some screenshots:
[http://img65.imageshack.us/img65/2177/kuvakaappausar4.png](http://img65.imageshack.us/img65/2177/kuvakaappausar4.png)
[http://img403.imageshack.us/img403/7483/kuvakaappaus3yl7.png](http://img403.imageshack.us/img403/7483/kuvakaappaus3yl7.png)

Grp card: Nvidia gf 6600 gt

Is it broken or just probs with linux?

---

### Post by hikaricore on 2007-08-11
Which driver are you using?

```
cat /etc/X11/xorg.conf | grep Driver
```

Should return something like this:

>     Driver         "kbd"
    Driver         "mouse"
    Driver         **"nvidia"**

If it returns **nv** that's the problem.

Also are you running WoW in opengl or d3d mode?

---

### Post by GvsE on 2007-08-11
It returns Driver "nvidia" and where i check that am i running it opengl or d3d?

---

### Post by hikaricore on 2007-08-11
> **GvsE said:**
> It returns Driver "nvidia" and where i check that am i running it opengl or d3d?

WoW defaults to d3d mode.

Try launching WoW with:

**wine WoW.exe -opengl**

Or edit your Config.wtf file to opengl.

---

### Post by GvsE on 2007-08-11
i have setted it to SET gxApi "OpenGL" :/

---

### Post by Sammi on 2007-08-11
You can always try the nuke approach, by reinstalling your Nvidia drivers.

---

