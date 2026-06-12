---
title: "3d acceleration?"
date: 2006-01-13
forum: General Help
---

### Post by sebweb on 2006-01-13
I just installed cedega but i failed one of my tests 3d acceleration. it said that my graphic card appeared not to be setup correctly. how do i set it up corectly

---

### Post by sethmahoney on 2006-01-13
[QUOTE=sebweb]I just installed cedega but i failed one of my tests 3d acceleration. it said that my graphic card appeared not to be setup correctly. how do i set it up corectly[/QUOTE]

Depends, what graphics card do you have?

---

### Post by sebweb on 2006-01-13
ati rage 128

---

### Post by Mr_Grieves on 2006-01-13
ATI is not the most Linux friendly thing in the world I'm afraid..

But let's have a go..
First off.. try and install the ATI driver.

```

sudo apt-get install fglrx-driver

```

If this does not work.. let's try reading abit.


ATIs Linux driver: [http://www.ati.com/support/driver.html](http://www.ati.com/support/driver.html) 
Official ATI+Linux Howto: [http://www.rage3d.com/content/articles/atilinuxhowto/](http://www.rage3d.com/content/articles/atilinuxhowto/) 
Linux-Gamers ATI+Linux Howto: [http://www.linux-gamers.net/modules/wfsection/article.php?articleid=22](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=22) 
Official ATI+Linux FAQ: [http://www.ati.com/products/catalyst/linux.html](http://www.ati.com/products/catalyst/linux.html) 
Official ATI+Linux forum: [http://www.rage3d.com/board/forumdisplay.php?f=61](http://www.rage3d.com/board/forumdisplay.php?f=61)

---

### Post by sebweb on 2006-01-13
It said 

Reading package lists... Done
Building dependency tree... Done
Package fglrx-driver is a virtual package provided by:
  xorg-driver-fglrx 6.8.0-8.16.20-0ubuntu16.1
You should explicitly select one to install.
E: Package fglrx-driver has no installation candidate

what next

---

### Post by Mr_Grieves on 2006-01-13
```

sudo apt-get install xorg-driver-fglrx

```

---

### Post by sebweb on 2006-01-13
now what

---

### Post by Mr_Grieves on 2006-01-13
[QUOTE=sebweb]now what[/QUOTE]
Check if 3D accel is working.
You may need to restart you computer or atleast X.org.

---

### Post by sebweb on 2006-01-13
thank you

---

### Post by Mr_Grieves on 2006-01-13
[QUOTE=sebweb]thank you[/QUOTE]
Is it working? :)

---

