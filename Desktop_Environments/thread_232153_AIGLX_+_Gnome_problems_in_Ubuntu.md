---
title: "AIGLX + Gnome problems in Ubuntu"
date: 2006-08-08
forum: Desktop Environments
---

### Post by juicymixx on 2006-08-08
Hey, I just installed dapper drake on an old dell latitude.   Install went great.   Then I decided to put in AIGLX + compiz as per:
[http://corvillus.com/2006/08/03/how-to-set-up-aiglx-and-compiz-on-ubuntu-606-running-gnome/](http://corvillus.com/2006/08/03/how-to-set-up-aiglx-and-compiz-on-ubuntu-606-running-gnome/)
and
[http://ubuntuforums.org/showthread.php?t=145068](http://ubuntuforums.org/showthread.php?t=145068)

well, after set up, just after the login screen gnome resets (like it's hit some fatal error or something).   So pretty much I can only log in over and over again.   The culprit seems to be this addition to my /etc/X11/xorg.conf :
Section "Extensions" 
Option "Composite" "Enable" 
EndSection

When I comment this out, gdm starts fine (however no eye candy of course)...   Any ideas about what I could try?:-({|= 

Thanks.

---

### Post by darrenm on 2006-08-08
Sure the onboard VGA is even up to the job of running opengl?

---

### Post by juicymixx on 2006-08-08
probably not (?)
I just wanted to see how far I could push it.

Anyone know of anything I could try?

---

