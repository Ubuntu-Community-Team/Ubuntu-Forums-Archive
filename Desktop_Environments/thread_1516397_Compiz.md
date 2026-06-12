---
title: "Compiz"
date: 2010-06-23
forum: Desktop Environments
---

### Post by Forming on 2010-06-23
I tried compiz-check and it shows that everything is ok.
[[IMG]http://www.part.lt/img/cdad5da2121b2680b8acaffc029cd48a917.png[/IMG]]("http://www.part.lt/perziura/cdad5da2121b2680b8acaffc029cd48a917.png")
But i try to enable it it writes :
[[IMG]http://www.part.lt/img/d57a7e0e2fbc10e7b5608b4c0870b306174.png[/IMG]]("http://www.part.lt/perziura/d57a7e0e2fbc10e7b5608b4c0870b306174.png")
Can someone tell me whats wrong?

---

### Post by lifeSum on 2010-06-23
What is the out put when you type:
```
compiz
```in the terminal?

---

### Post by Forming on 2010-06-24
This :
[[IMG]http://www.part.lt/img/95945585b54c726103dbdaade1cae1e57.png[/IMG]](http://www.part.lt/perziura/95945585b54c726103dbdaade1cae1e57.png)

---

### Post by lifeSum on 2010-06-25
Try running this in a terminal:

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo dpkg-reconfigure xserver-xorg

```This reconfigures the config for X11. The first line creates a backup of the config file in case something goes wrong (it shouldn't, though).

Compiz was always a pain for me to get working. Hopefully this will do the trick.

---

### Post by andrea000 on 2010-06-25
> **Forming said:**
> This :
[[IMG]http://www.part.lt/img/95945585b54c726103dbdaade1cae1e57.png[/IMG]](http://www.part.lt/perziura/95945585b54c726103dbdaade1cae1e57.png)

There is no whitelisted driver found do you know the video card
and driver you have?

---

### Post by lifeSum on 2010-06-25
> **andrea000 said:**
> There is no whitelisted driver found do you know the video card
and driver you have?

It appears he has a SIS video card, and is using the sis driver. (this was outputted from the ./compiz-check originally posted). Unfortunately, I have no experience with sis cards. Any ideas?

---

### Post by Forming on 2010-06-25
*I've changed my ubuntu version to 9.10 , but still have problems with compiz if u want to help heres the thread : [http://ubuntuforums.org/showthread.php?p=9504202#post9504202](http://ubuntuforums.org/showthread.php?p=9504202#post9504202)*

---

