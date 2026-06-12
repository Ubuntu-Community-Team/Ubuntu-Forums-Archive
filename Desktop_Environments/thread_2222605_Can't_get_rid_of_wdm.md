---
title: "Can't get rid of wdm"
date: 2014-05-07
forum: Desktop Environments
---

### Post by Caeru_Lean on 2014-05-07
I have a minimal installation of Ubuntu 14.04 with dwm as window manager.
The display manager wdm was installed as a dependency and is launched at every boot. But I want a manual login to X with startx (.xinitrc is configured with exec dwm).

[LIST]
[*]I disabled the service wdm using bum, but when I launch startx I got the error message
> Only root wants to run wdm
[*]The same error message appears after removing wdm completely with its dependencies.
[*]I also modified in vain the parameter splash quiet of /etc/default/grub to text.
[/LIST]
I used to setup Debian and ArchLinux systems without having this problem. Is it specific to Ubuntu? What is the proper way to resolve my issue? I hope there won't be a confusion concerning the couple wdm/dwm ...

---

### Post by bapoumba on 2014-05-07
Although old, may be here [http://ubuntuforums.org/showthread.php?t=1053814](http://ubuntuforums.org/showthread.php?t=1053814) ?
Looks like the link is dead, probably was something close to : [http://dwm.suckless.org/](http://dwm.suckless.org/)

Now I do not see anything related to wdm as a dependency to dwm : [http://packages.ubuntu.com/trusty/dwm](http://packages.ubuntu.com/trusty/dwm)

---

### Post by ibjsb4 on 2014-05-07
I also went down a couple of levels and not seeing where dwm depends on wdm.  Could you have a ppa messing with you?

---

### Post by bapoumba on 2014-05-07
> **ibjsb4 said:**
> I also went down a couple of levels and not seeing where dwm depends on wdm.
Did that too, and there is no wdm-named package :)

---

### Post by Caeru_Lean on 2014-05-16
Thank you for your replies.

May be I installed the complete Xorg meta package.
I don't remember, but I did a fresh minimal install in the meantime.
Everything works fine now.

---

### Post by bapoumba on 2014-05-16
OK :)
Please mark your thread as solved (under Thread Tools), it may help others, thanks !

---

