---
title: "New Wave Theme makes power button disappear!"
date: 2011-09-08
forum: Desktop Environments
---

### Post by thatsmyboy on 2011-09-08
Occasionally when I login to my account I notice that the Indicator Applet Session applet ( aka the power button ) has somehow been pushed off the screen. It doesn't seem to happen every time, but when it does I've been forced to shut down manually by using the power button on the machine ( or use the "sudo gdm stop" method to get out of gnome and relogin ). I recently realized that another workaround is just going into the system preferences and temporarily switching my theme which will reload all the applets / interface. *much easier btw* 

Anyone have ideas on tracking this down? Or perhaps even fixing it??:)

---
Dell C521, Ubuntu 10.04 LTS, no hw acceleration so defaults to plain old gnome

Seems like the issue is similar to this one : [http://ubuntuforums.org/showthread.php?t=1428740](http://ubuntuforums.org/showthread.php?t=1428740)

---

### Post by thatsmyboy on 2011-09-08
really?? No takers? :confused:
how about a few screenshots!
[IMG]http://i53.tinypic.com/14j696q.png[/IMG]
[IMG]http://i56.tinypic.com/358t1cw.png[/IMG]

---

### Post by thatsmyboy on 2011-09-12
Bump!!!!

---

### Post by Frogs Hair on 2011-09-12
I had a problem with that theme ,  I could not open Nautilus because the theme caused a broken link to the desk top and  I later found a bug report . I ended up completely  removing  and and reinstalling the gnome-themes-ubuntu package .

After reinstalling the package I removed the New wave theme from the usr/share/themes folder . I found the problem because Nautilus would not open . When using gksu nautilus the terminal displayed the broken link error . That is also the first time I had used that theme since 9.10 .

---

### Post by thatsmyboy on 2011-09-23
sadly, I can now report that this STILL occurs with the Ambiance theme (another login). Repeat, this issue is not limited to New Wave Theme

[IMG]http://i51.tinypic.com/33cwzh4.png[/IMG]

---

