---
title: "Help to configure Logitech mouse..."
date: 2009-04-08
forum: General Help
---

### Post by BluBird302 on 2009-04-08
Hey guys, I am a newbie to Ubuntu 8.10 and so far I am liking it (long time windoz user). I seem to have a problem with trying to figure out how to configure my LX3 Logitech optical mouse, of course I tried their website but no Linux drivers. I have read several posts on here but still cannot get it figured out. Everything on the mouse seems to work except for the left and right slide buttons on the scroll wheel. I have read to check the xorg.conf file for the imput and edit, but on my file it doesn't show the input for the mouse. I have tried imwheel but not really sure how to set that up either, and also ran the sudo dpkg-reconfigure -phigh xserver-xorg command and the results below is what I have. I mainly want to get these buttons to work for Firefox 3, to forward and go back through the pages, but have been unsuccessful so far. I'm not sure what information you guys need so please ask and I will do the best I can, is there something I'm missing here?


Section "Device"
Identifier "Configured Video Device"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection

---

### Post by ender4 on 2009-04-09
i am also having the same trouble with my Lx 8,  the side buttons work fine with firefox 3 but on everything else they don't do anything.  from the comments in xorg.conf i would assume that the reason that you can't change the settings from there is that the x server now autamates tasks (such as mouse configuration) that were formerly done by xorg.conf, how to change that now i do not know.  

I've tried changing keyboard shortcuts to work with mouse clicks, but have been unsuccessful

---

### Post by BluBird302 on 2009-04-09
Thanks for the reply, I still have not figured it out.  I have tried adding the "input" section to xorg but still no effect.  It has mouse options in the preferences but none for mouse buttons, may be someone else will come across this thread and give some advice.

---

### Post by speedwell68 on 2009-04-09
I found this thread on the subject.  The last poster seems to feel he has come up with a solution.  I hope it helps.:D

---

### Post by BluBird302 on 2009-04-11
> **speedwell68 said:**
> I found this thread on the subject.  The last poster seems to feel he has come up with a solution.  I hope it helps.:D

Hey speedwell68, you said you found "this" thread on the subject, did you mean the one we are talking about or another thread?  I didn't see one posted on your reply, I still have not found a solution to this as of now, thanks.

---

