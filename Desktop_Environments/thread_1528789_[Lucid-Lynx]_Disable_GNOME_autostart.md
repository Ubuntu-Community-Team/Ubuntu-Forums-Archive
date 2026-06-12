---
title: "[Lucid-Lynx] Disable GNOME autostart"
date: 2010-07-11
forum: Desktop Environments
---

### Post by JHSL on 2010-07-11
Hi,

How can you disable GNOME autostart in lucid, so it can be started only when i need it?


/JHSL

---

### Post by bobcollard on 2010-07-12
> **JHSL said:**
> Hi,

How can you disable GNOME autostart in lucid, so it can be started only when i need it?


/JHSL
    If you are referring to the desktop Gnome and you have another desktop installed like KDE or Xfce, then you can change it at login in "Settings" and the next time you startup the previous desktop will open.
   If you meant Application autostart then you can uncheck the applications you don't want, though you must be careful which ones you remove.

---

### Post by JHSL on 2010-07-12
Hi,

To clarify what I mean.

- When the machine starts the GNOME loginscreen appears, here it is possible to choose the user and password, and the session (GNOME, failsafe GNOME, xterm)
- When xterm is chosen then run startx or something when I need the graphical desktop


//JHSL

---

### Post by bobcollard on 2010-07-12
> **JHSL said:**
> Hi,

To clarify what I mean.

- When the machine starts the GNOME loginscreen appears, here it is possible to choose the user and password, and the session (GNOME, failsafe GNOME, xterm)
- When xterm is chosen then run startx or something when I need the graphical desktop


//JHSL
You want to startup in Terminal?  See this thread:
[http://ubuntuforums.org/showthread.php?t=1519013&highlight=startup+terminal](http://ubuntuforums.org/showthread.php?t=1519013&highlight=startup+terminal)

---

### Post by JHSL on 2010-07-12
Hi,

That got me almost there, but the only way I can get it to not start GNOME, is to start in failsafe mode and then choose resume normal boot

//JHSL

---

### Post by bobcollard on 2010-07-12
> **JHSL said:**
> Hi,

That got me almost there, but the only way I can get it to not start GNOME, is to start in failsafe mode and then choose resume normal boot

//JHSL
The only other thing I can think of is some distros start from ttl like the one at this link:

[http://www.minimalinux.org/ttylinux/](http://www.minimalinux.org/ttylinux/)

You can build from this.

---

