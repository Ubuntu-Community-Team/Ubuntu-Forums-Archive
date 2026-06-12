---
title: "Starts up with grey theme"
date: 2010-12-21
forum: Desktop Environments
---

### Post by TheMegaIdiot on 2010-12-21
[IMG]http://uploadir.com/u/f7702492[/IMG]

Hello,

Some times when I start up I get this theme activated and used. The only way to get rid of it totally is to restart.

How can I stop this?

Jack.

---

### Post by oostue on 2010-12-21
next time don't restart your machine, open a terminal and type "*sudo **killall gnome*-[I]panel"
[/I]This will close out the theme (gnome panel) and auto restart it. This is not a fix just a work around. 
Reinstalling or doing an upgrade on gnome panel might fix the problem.

---

### Post by TheMegaIdiot on 2010-12-21
> **oostue said:**
> next time don't restart your machine, open a terminal and type "*sudo **killall gnome*-[I]panel"
[/I]This will close out the theme (gnome panel) and auto restart it. This is not a fit just a work around. 
Reinstalling or doing an upgrade on gnome panel might fix the problem.

Thanks, I'll try that next time it happens.

---

### Post by susema on 2010-12-21
I've got same and I'll try, too. Thanks..

---

### Post by TheMegaIdiot on 2010-12-21
Tried this as it happened again when I booted up, it just restarted the desktop with the same theme.

---

### Post by susema on 2010-12-21
I tried everything, reset panel and gnome settings, removing ubuntu-desktop, reinstalling ubuntu-desktop, gdm, etc, etc...  My distribution is Natty..

But, same theme :(

---

### Post by gogolink on 2010-12-21
Try what happens when you just go to System > Preferences > Appearance -- without even changing anything in appearance:

Whenever I've had that grey theme, it would then revert to my actual theme (usually some variation of Bisigi's Exotic theme).

I think your problem is the same that is discussed [here]("http://ubuntuforums.org/showthread.php?t=1575703"); without a full solution yet.

I've had that problem, but only on a MacIntel with 1GiB memory; haven't had any comparable problem on my 2GiB Toshiba.

---

### Post by susema on 2010-12-22
I unfortunately reinstalled Ubuntu, because realy tried everything, but :(

---

### Post by rookcifer on 2010-12-22
This is a major bug that I don't think the Ubuntu team knows how to fix.  Does anyone know if there is even a bug report for this?  It has been going on far too long now.

---

### Post by bradshawd on 2010-12-23
Yes there is a Bug..  I believe it is this one [https://bugs.launchpad.net/bugs/588155](https://bugs.launchpad.net/bugs/588155)

Derek

---

