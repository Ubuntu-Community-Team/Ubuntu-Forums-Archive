---
title: "Gnome Appearance / Theme issue."
date: 2008-08-01
forum: Desktop Environments
---

### Post by Sean-Michael on 2008-08-01
I run into issues when I try change and costumize my themes threw the appearances manager.

1. Theme previews are not shown as I would expect.
[ATTACH]79704[/ATTACH]

2. When I try to cosumize my theme I get this...
[ATTACH]79705[/ATTACH]

and...
[ATTACH]79706[/ATTACH]

Makes it hard to customize things and sometimes I have to restart for the effects to take effect.  Only the Gtk-ChTheme really seems to work.

Serval Performance(System76), GeForce 8600M GT 512 MB, AMD64 Ubuntu 8.04, Core 2 Duo T7700 2.4 GHz,

Thanks in advance for help!
Sean-Michael.

---

### Post by doublemeat on 2009-01-11
I noticed something similar.  The "Appearance Preferences" applet used to work, as it did for all my Ubuntu installations.  For this one particular installation of 8.10 x64, I also installed the "gtk-chtheme" applet.  Ever since then, Appearance Preferences no longer works--similar to what you described.  Even doing a full removal of gtk-chtheme, and a reboot, did nothing to restore it.  Now my only option is to reinstall gtk-chtheme, and use that.  Only prob is it isn't as customizable as Appearance Preferences is!  Sucks...

---

### Post by doublemeat on 2009-01-11
> **doublemeat said:**
> I noticed something similar.  The "Appearance Preferences" applet used to work, as it did for all my Ubuntu installations.  For this one particular installation of 8.10 x64, I also installed the "gtk-chtheme" applet.  Ever since then, Appearance Preferences no longer works--similar to what you described.  Even doing a full removal of gtk-chtheme, and a reboot, did nothing to restore it.  Now my only option is to reinstall gtk-chtheme, and use that.  Only prob is it isn't as customizable as Appearance Preferences is!  Sucks...

After much searching I found the solution (obliquely):

```
sudo aptitude purge gtk-chtheme
sudo aptitude purge gtk-qt-engine
rm ~/.gtkrc-2.0
```The last line was the part I was missing.  Control will not be restored to Appearance Preferences without removing ~/.gtkrc-2.0!

):P

---

### Post by Sean-Michael on 2009-01-12
Many thanks to you for coming back and sharing!

I had been avoiding the appearance manager since my original post.

Again, thank you!

---

