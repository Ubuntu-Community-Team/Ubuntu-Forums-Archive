---
title: "no desktop - x server error"
date: 2007-03-20
forum: Desktop Environments
---

### Post by stavpal on 2007-03-20
Hi! I've installed ubuntu 6.10 and at a point was messing up with synaptic. I selected suspend and when I rebooted I got a x server error and no gnome
[[IMG]http://img141.imageshack.us/img141/9146/dscn2171nd8.th.jpg[/IMG]](http://img141.imageshack.us/my.php?image=dscn2171nd8.jpg)
I tried reinstalling the nvidia drivers but I get the same error!
What can I do?
Thanks in advance!

edit: I had selected in synaptic some [base, base[restricted]] {i686, generic etc...}....that probably caused the problem, but how do I fix it?

---

### Post by Mrwasab1 on 2007-03-20
if you can get to a command line have you tried typing 

```
sudo dpkg-reconfigure xserver-xorg
```

seems from that error message that something went wrong in the xorg file and it didnt like it.

the above code will let you reconfigure it

not sure, i am fairly new myself but ive messed up that file before and this fixed it

---

### Post by stavpal on 2007-03-20
Ok I'll try it. I was trying to optimize it for the cpu (pentium4). Does anyone know what packets do I need to enable and/or disable for maximum optimization (speed) (in synaptic)?

---

