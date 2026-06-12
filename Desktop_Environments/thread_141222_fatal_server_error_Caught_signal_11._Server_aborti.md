---
title: "fatal server error: Caught signal 11. Server aborting."
date: 2006-03-07
forum: Desktop Environments
---

### Post by catSplatt on 2006-03-07
I am going to take a stab at this and say it is a driver error when trying to start gnome.

This is a fresh install and I have not played with anything.

In the Xorg.0.log file:
'LoadModule: mga_hal' seems to fail.

I even tried loading the live version and X server fails when trying to start Gnome.

I am a 12 year veteran of windows systems and enterprise networks but a newbie trying to learn a linux distro... so far this is a bad start.

I need a step by step on how to load the correct driver from a command prompt in ubuntu as I do not know very much about linux to begin with. the card is a Matrox G450, AGP, 32mb.

Any pointers would be appreciated. Thanks much!

~catSplatt

---

### Post by catSplatt on 2006-03-07
...changing the driver type to vesa seemed to do the trick.

thanks Ramses de Norre.

---

### Post by desjazz on 2006-10-21
I have the same error and have tried to change the driver to vesa adn this has not worked. I have tried to run the 855resolution fix and that has not worked. I have been tot he Dell website to get the exact refresh rates for the monitor I am using and I still haven't got anywhere. Can someone please guide me in the right direction?

---

### Post by guila on 2007-01-08
In order to prevent problems in the future, try backing up your working xorg.conf:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.org
```

.org for origional file. This may be of help in the future as a referance.

.bak for backup.

You can restore from back up at any time with:

```
sudo cp /etc/X11/xorg.conf.org /etc/X11/xorg.conf
```


-[http://ubuntuforums.org/showthread.php?t=269052]("http://ubuntuforums.org/showthread.php?t=269052")

---

