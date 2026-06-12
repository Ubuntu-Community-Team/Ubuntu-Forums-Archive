---
title: "Nvidia GeForce 7800GT games problem"
date: 2006-07-11
forum: Gaming &amp; Leisure
---

### Post by Luco on 2006-07-11
So i have this graphycs card and i'm using ubuntu 6.06 (i386). I installed the drivers... which i'm not sure they work properely.

I get the nvidia logo on logon screen, but glxgears work very badly. I get this error:

```
X connection to :0.0 broken (explicit kill or server shutdown).
```

any ideas?

---

### Post by frodon on 2006-07-11
Could you post your xorg.conf file for more informations ?
```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by Luco on 2006-07-11
ok, I did mess up my X11 config... so I just reinstalled Ubuntu and it works perfect :) .

Thank you anyway.

---

### Post by ironfistchamp on 2006-07-11
When I mess up my config I run 

sudo dpkg-reconfigure xorg-xserver

or is it the other way around. I can never remember.

---

