---
title: "Acer Aspire 5600 display resolution issue"
date: 2006-09-14
forum: Desktop Environments
---

### Post by ampop on 2006-09-14
Hello,

On laptop Acer Aspire 5600, the maximum display resolution that I have on Ubuntu it's 1024x768. The maximum resolution specification for my laptop it's 1280x800.
I allready tried a lot of xorg.conf configurations, I follow the procedures from several posts from this forum
[http://ubuntuforums.org/showthread.php?t=131648](http://ubuntuforums.org/showthread.php?t=131648)
[http://ubuntuforums.org/showthread.php?t=89727](http://ubuntuforums.org/showthread.php?t=89727)
[http://ubuntuforums.org/showthread.php?t=244488](http://ubuntuforums.org/showthread.php?t=244488)
[http://ubuntuforums.org/showthread.php?t=246152](http://ubuntuforums.org/showthread.php?t=246152)
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)
and much more.
Nothing works. ](*,) 

There is anyone with the same laptop than me, that can show his /etc/X11/xorg.conf ?

Thank you.

---

### Post by ampop on 2006-09-15
> **ampop said:**
> Hello,

On laptop Acer Aspire 5600, the maximum display resolution that I have on Ubuntu it's 1024x768. The maximum resolution specification for my laptop it's 1280x800.
I allready tried a lot of xorg.conf configurations, I follow the procedures from several posts from this forum
[http://ubuntuforums.org/showthread.php?t=131648](http://ubuntuforums.org/showthread.php?t=131648)
[http://ubuntuforums.org/showthread.php?t=89727](http://ubuntuforums.org/showthread.php?t=89727)
[http://ubuntuforums.org/showthread.php?t=244488](http://ubuntuforums.org/showthread.php?t=244488)
[http://ubuntuforums.org/showthread.php?t=246152](http://ubuntuforums.org/showthread.php?t=246152)
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)
and much more.
Nothing works. ](*,) 

There is anyone with the same laptop than me, that can show his /etc/X11/xorg.conf ?

Thank you.
I solved my issue with this post: [http://ubuntuforums.org/showthread.php?p=1501028#post1501028](http://ubuntuforums.org/showthread.php?p=1501028#post1501028)

---

### Post by web-man on 2007-05-01
but i don't have a nvidia, i have intel incorporated graphic

What can i do? :confused:

---

### Post by Rinnan on 2007-05-06
sudo apt-get install 915resolution (when it's done, reboot)

This works in Edgy, Feisty.  You need universe repository enabled.  I have an Acer Aspire 5600 and this is what I did (same graphics chipset as well)

Good luck, tell me if it works.

---

### Post by wrongOne on 2007-10-23
Rinnan you saved me!!!!! thx so much my eyes were starting to hurt from blurry lettering and large ...everything!

Could you briefly explain exactly what it is that command did? Im relatively new to Linux so i am just trying to gain some fundamental understanding of what commands are doing....

For anyone else experiencing a display problem (resolutions being stuck at 1024x768) on an Acer Aspire 5600 can breath a sigh of relief thanks to Rinnan, this worked for my box and will presumably work for yours :D

---

