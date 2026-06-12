---
title: "kde display configuration forgetfulness"
date: 2005-12-26
forum: General Help
---

### Post by gts on 2005-12-26
I have a 19'' monitor, and its ideal configuration is 1280x1024 @ 100 Hz.
Every time I reboot my PC, the refresh rate changes from 100 Hz to 85 Hz... If I check "apply settings on kde startup", after the next reboot also the resolution changes (from 1280 x 1024 to 1024 x 768).

I suppose there is a file that is modified by gui display configuration tool, so is there a KDE (not xorg.conf) configuration file that contains the current refresh rate and resolution? 

Maybe modifying it by hand can help me...

---

### Post by mlomker on 2005-12-26
[QUOTE=gts]Maybe modifying it by hand can help me...[/QUOTE]

AFAIK everything is done in the xorg.conf file.  There's a [how-to]("http://www.ubuntuforums.org/showthread.php?t=83973") on creating a modeline if you haven't already done so.

---

