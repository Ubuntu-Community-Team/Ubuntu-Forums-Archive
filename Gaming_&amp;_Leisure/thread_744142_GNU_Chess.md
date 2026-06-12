---
title: "GNU Chess"
date: 2008-04-03
forum: Gaming &amp; Leisure
---

### Post by mahbub.red_devil on 2008-04-03
i can not get 3d support on GNU chess.
when i try to get 3d support, it shows the errors

" Unable to enable 3D mode
You are unable to play in 3D mode due to the following problems:
No Python OpenGL support
No Python GTKGLExt support"

how can i enable 3d support?

---

### Post by nebu on 2008-04-03
install the python-opengl and libgtkglext1 packages....

> sudo apt-get install python-opengl
sudo apt-get install libgtkglext1

---

### Post by ozymo on 2008-04-06
Hey.

I had the same issue, even after installing the above packages.  I have to install python-gtkglext1:

```
sudo apt-get install python-gtkglext1
```

Now, I have the crappy 3D view working (albeit, I still use the 2D view because it's better imho).

Thanks,
/cs
[~chuck/blog]("http://www.ozymo.com/~chuck/blog")

---

### Post by Treelova on 2008-12-01
Thanks both the suggestions worked for me

---

### Post by alchemist0 on 2008-12-07
Thanx! ;)

---

### Post by gamorgan on 2009-04-29
These packages worked, but it now fails to load, and crashes everytime. nVidia GeForce Go 7600 laptop, running 173 drivers. Previously had trouble with 180 drivers. Any ideas?

Gabe

---

### Post by lefontiy on 2009-05-01
> **gamorgan said:**
> These packages worked, but it now fails to load, and crashes everytime. nVidia GeForce Go 7600 laptop, running 173 drivers. Previously had trouble with 180 drivers. Any ideas?

Gabe
Same video card - same issue with crashes... :(

---

### Post by mohammad90 on 2009-05-02
nvidia GeForce 8400M GS ... same problem and crashes,,, any help ?

---

### Post by malachi1990 on 2009-05-02
I think this is a problem in the packaging for ubuntu, as I have the same problem throughout several versions (since 8.04, and im on 9.04).  

But I have it working perfectly in sabayon.

---

### Post by TheBuzzSaw on 2009-05-03
Same here.

Nvidia 8500 with 180 driver...

Now it crashes upon loading. :(

---

### Post by PGScooter on 2009-06-25
these three packages worked for me (no crashes yet) with the following card:
Graphics: 512 MB DDR2 nVidia GeForce G105M

---

### Post by afroman10496 on 2009-09-05
Solution (sorry for bump, mods please don't arrest me:P)

```
sudo apt-get remove python-opengl
sudo apt-get remove libgtkglext1 
```

---

