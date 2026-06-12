---
title: "xubuntu - how to make transparent windows"
date: 2007-02-13
forum: Desktop Environments
---

### Post by jeisma on 2007-02-13
hi!

in xubuntu 6.10, how do you setup transparent windows? 

similar to some screen shots in xfce.org?


thanks!

joey

---

### Post by kerry_s on 2007-02-13
You need to turn composite on by putting this line in your /etc/X11/xorg.conf->

```
Section "Extensions"
    Option         "Composite" "True"
EndSection
```
 
You also have to be running the latest xfce 4.4.0, you can get that by adding the repo->

```
deb [http://ubuntu.tolero.org/](http://ubuntu.tolero.org/) edgy xfce-4-4-0
```

---

