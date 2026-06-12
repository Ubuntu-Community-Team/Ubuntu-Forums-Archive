---
title: "GDM stop, KDM start [Resolved]"
date: 2006-02-26
forum: Desktop Environments
---

### Post by Mis_Uszatek on 2006-02-26
Hello everyone

I have installed KDE, and I would like to switch (I'm not quite sure) 'login managers'. Actually I'm using GDM, and I would like by default KDM. 
I remember there was this question during installation KDE from repositories, but I don't have any idea why I have choosen GDM(?)

Thanks for help.

---

### Post by fdoving on 2006-02-26
Open a terminal and run: 'sudo dpkg-reconfigure kdm'

- Frode

---

### Post by Xian on 2006-02-26
You can select either using this command from a terminal:
$ sudo dpkg-reconfigure gdm

If you know you never want gdm just remove it in Synaptic.
No use keeping it if it will never be accessed.

---

### Post by aysiu on 2006-02-26
You could also do ```
sudo nano /etc/X11/default-display-manager
``` and change ```
/usr/sbin/gdm
``` to ```
/usr/bin/kdm
```

---

### Post by Mis_Uszatek on 2006-02-27
Thank you all very much.
KDM works by default now.

---

### Post by CowzRule on 2007-01-05
> **aysiu said:**
> You could also do ```
sudo nano /etc/X11/default-display-manager
``` and change ```
/usr/sbin/gdm
``` to ```
/usr/bin/kdm
```Exactly what I was looking for!!! Thanks A Bunch!!!

---

