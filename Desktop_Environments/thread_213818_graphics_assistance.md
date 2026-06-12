---
title: "graphics assistance"
date: 2006-07-11
forum: Desktop Environments
---

### Post by tunads on 2006-07-11
i was attempting to help a friend install ubuntu, and his computer is soooo slow that it could not run the live cd efficiently enough to install the os, so in a last ditch effort to install the os I hooked his hard drive up to my pc and installed it this way.  now i figured there was going to be problems when i use this install on his pc, one of which i have run into.  you see, my pc has an fairly new nvidia graphics card, while my friend has integrated graphics that came with his archaic intel chipset (i'm not sure which chipset he has, but the processor is an intel celeron that runs at 366Mhz, if that helps).  So when i started ubuntu for th first time everything loaded properly, except just before it went to the login screen, a blue popped up that said the graphics were not configured properly.  Now i have seen this problem before, but since, at the time, it was a fairly fresh install, i just reinstalled ubuntu to fix the problem.  I don't have that option with this system, because it can't handle running the live cd.  

a few other details:
i can boot into recovery mode.
i am also a fairly new user myself, and recovery mode scares the hell out of me so PLEASE keep your explanations acceptable for 'dumb' people.

thanks for any help in advance!!!!!!!!!!!!!!

---

### Post by Dr. Nick on 2006-07-11
Yeah your xorg.conf is messed up since the cards are totally differnent
try this command from the command line, if you are in recoveryt mode then sudo isnt necessary, but if you just boot like normal and bypass the error until you are at a text logn, then login and use sudo in the following command

[COLOR=#0000DF][B]sudo dpkg-reconfigure xserver-xorg
[COLOR=Black]
The defaults are usually safe, just slow down on the video card selection and make sure it looks good, if you cant decide which driver to choose go with "vesa"[/COLOR]

[/B][/COLOR]

---

### Post by tunads on 2006-07-11
you the man!!!!!!!!!!!!!!
thanks a lot

:-)

---

