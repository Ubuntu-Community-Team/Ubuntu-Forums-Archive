---
title: "Beryl - Unable to login to desktop enviro."
date: 2007-01-30
forum: Desktop Environments
---

### Post by drumfish on 2007-01-30
Hi, I'm running the Beryl 2.0 beta for my desktop. I have set to run from startup (session option) anyway, when messing with some of the XGL settings it froze my desktop. I rebooted and now I boot to a halted screen. I do get as far as the splash screen and app loader loading a few items in startup but that's about it. 

I checked the wiki (kick *** info. in there by the way) and  I've ran the following commands.

cd ~/.config/autostart
rm beryl-manager.desktop beryl-xgl.desktop

I still boot to a blank desktop. I do get a mouse cursor though. 

I've also tried some others but get the file can not be found etc. or similar.

rm -f ~/.config/autostart//beryl-manager.desktop

](*,) 

Any ideas? 

Thanks.

:wink:


* I got it running nevermind! I had to restart the X session, duh

---

### Post by zitanos on 2007-01-31
can you do me a favor and post your xorg...thanks...

i think i may have something missing from my xorg

---

### Post by Nemix77 on 2007-03-02
OK, I got the same problem right click on beryl and set it XGL and now can't do anything except move the mouse.  Can you tell exactly what you did.

---

