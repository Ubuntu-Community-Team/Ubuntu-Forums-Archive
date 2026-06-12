---
title: "botched mac emulation on 7.10!"
date: 2007-11-15
forum: Desktop Effects &amp; Customization
---

### Post by jalirious on 2007-11-15
Hi, I tried the steps in this guide;

[http://www.howtoforge.com/mac4lin_make_linux_look_like_a_mac](http://www.howtoforge.com/mac4lin_make_linux_look_like_a_mac)

was sick of it by page 4, went back to undo the steps. My number of destops was stuck at 2, despite saying in preferences that there were 4 columns -> so change it in ccsm.

Ahh. ccsm wasn't there anymore. Tried to reinstall it - blocked due to this problem;

[http://ubuntuforums.org/showthread.php?t=580063](http://ubuntuforums.org/showthread.php?t=580063)

so commented out these in my /etc/apt/sources.list

#deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
#deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
## Avant Window Navigator
#deb [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) feisty avant-window-navigator
#deb-src [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) feisty avant-window-navigator

And uninstalled completely - reinstalled everything compiz (including libraries)
reinstalled emerald.

Ccsm worked -> set the number of desktops to 4. No cube joy. Also I still have the crummy mac traffic lights on my terminals and my panel disappears when browsing, etc.

>compiz --replace 

does fail, but briefly restores headers. 

Considering system reinstall, any other ideas?

---

