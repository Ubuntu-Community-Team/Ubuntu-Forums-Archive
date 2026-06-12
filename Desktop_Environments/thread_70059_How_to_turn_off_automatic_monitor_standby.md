---
title: "How to turn off automatic monitor standby"
date: 2005-09-28
forum: Desktop Environments
---

### Post by recce101 on 2005-09-28
Whenever a period of several minutes passes with no user input, the monitor screen turns black and requires a keyboard stroke or (if a GUI is in use) keyboard stroke or mouse input before it will reactivate. This is true even for a bare-bones server installation with no desktop of any kind. I would like to be able to turn this power-saver (or whatever) feature off so the monitor display will remain on for extended periods. With no screensaver, KDE, Gnome, or XFCE settings to fiddle with, what can I do?

---

### Post by chalewa on 2007-02-15
I am wondering this too....

---

### Post by allwin on 2007-02-15
Me three!

---

### Post by kerry_s on 2007-02-15
You use xset, it's the built in power manager on most any distro.

xset -q    <to see what the settings are
xset +dpms   <turns power saving on
xset -dpms   <turns power saving off
xset s off off   <screen saver on/off, it go's time/cycle you can use # instead
xset dpms 0 0 300    <time till blank 300=5 min. the first two "0" is standby,suspend.
xset dpms force off   <turn off monitor now

man xset   <to learn more

---

### Post by rklauco on 2007-04-08
For me, the only option that worked was to go to session startup programs and add something like this:
/usr/bin/xset dpms force on

Using this settings, the TV on my home media center remains on even for 20 hours :-)

---

### Post by r00tintheb0x on 2007-04-08
system>preferences>power management ?

---

### Post by rklauco on 2007-04-08
> **r00tintheb0x said:**
> system>preferences>power management ?
No help - set to never turn the monitor off :-(

---

### Post by rklauco on 2007-04-08
Cechk [this thread]("http://ubuntuforums.org/showthread.php?t=347079"), especialy the hint from David_2001.

---

