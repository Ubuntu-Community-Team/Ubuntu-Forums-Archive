---
title: "remove KDE"
date: 2006-04-03
forum: Desktop Environments
---

### Post by DFreeze on 2006-04-03
I’ve installed KDE on my Ubuntu Breezy system, but without reading the forums/wiki properly. So I apt-getted the KDE environment from the repositories, and not the Kubuntu-package. Now I’ve got a way too cluttered GNOME menu, and a non-Ubuntized KDE, so I want to uninstall and do it right this time. Removing the KDE-metapackage in Synaptic only removes like 40 kB, so that doesn’t work. 

I know (by now) that there’s a way to have Kubuntu list the KDE apps in its menu and Ubuntu only the GNOME ones, so the menus don’t get cluttered. So that’s what I want to do, if I can reverse the KDE install. Or is reinstalling Breezy (in that case I’ll wait for Dapper) the only option.

Any suggestions?

---

### Post by KingBahamut on 2006-04-03
apt-get remove kdebase kde

---

### Post by DFreeze on 2006-04-04
Does that remove the all the software that comes with KDE as well? 

Sorry if its a dumb question, but I haven't had a chance to try it yesterday. Else I would've known by now.

---

### Post by aysiu on 2006-04-04
Do this:
[http://www.ubuntuforums.org/showthread.php?t=123969](http://www.ubuntuforums.org/showthread.php?t=123969)

this:
[http://www.ubuntuforums.org/showthread.php?t=59455](http://www.ubuntuforums.org/showthread.php?t=59455)

and then this: ```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```

---

### Post by DFreeze on 2006-04-05
I just tried the above suggestion (apt-get remove ...) but that only removed the two packages named, not the whole DE that synaptic installs when selecting KDE. Is there any way to just remove all the KDE cruft and start over?

Or should I just install a fresh dapper and do it right from the start?

---

### Post by JimmyJazz on 2006-04-10
[http://ubuntuforums.org/showthread.php?t=157897](http://ubuntuforums.org/showthread.php?t=157897)

I made a script for just this

---

