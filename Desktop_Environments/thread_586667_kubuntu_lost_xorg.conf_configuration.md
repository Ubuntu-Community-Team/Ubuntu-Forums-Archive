---
title: "kubuntu lost xorg.conf configuration"
date: 2007-10-22
forum: Desktop Environments
---

### Post by lugburz on 2007-10-22
I'm having some problem after an attemp to enable a 2nd monitor. II tried to change the XOrg configuration from the KDE system configuration module, probably some setting was wrong and I was not able to restart the X-server.

I tried using
```
$ sudo dpkg-reconfigure xorg
```

but seems that this doesn't work in gutsy.

So I tryied to remove the xorg.conf and xorg.conf.1 and xorg.conf.2 from /etc/X11 directroy. This solution was good beacuse the xserver now is on but: I lost the italian configuration of my keyboard and xorg.conf file down't exist anymore.

Why this strange behaviour?

---

### Post by miggols99 on 2007-10-22
The command should be

```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by lugburz on 2007-10-22
now is better... :):lol:

---

### Post by llangwm on 2008-06-10
When stuck in the command prompt I go to /etc/X11/
[LIST]
[*]do an ls to list the files there 
[*]you can then sudo mv (rename) one of the old, working xorg.conf.x files to xorg.conf
[*]then restart the xserver with startx.
[/LIST]

I too have only got into this sort of bother trying to get the dual monitor option working!

---

