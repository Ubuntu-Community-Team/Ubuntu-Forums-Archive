---
title: "Installing ATI Radeon 9200 on Kubuntu?"
date: 2006-04-18
forum: Desktop Environments
---

### Post by wreckingcru on 2006-04-18
Tried to follow the instructions via ATI's website with no change in resolution. I have a 15" LCD, my first - so I'm not sure if the damn thing supports higer than 1024x768. 

Is the resolution monitor dependant or video card dependant? 
Does the GUI (KDE) have any say in the whole thing?
I can't even get the config to change it's name to "ATI something" after running the ATI install.

Has anyone got suggestions/ideas/tips?

---

### Post by uteck on 2006-04-18
It may not support a higher res.  
I have not read the ATI instructions when I did it.  I just installed the restricted-modules package with apt and changed the driver from ati to fglrx in xorg.conf.  It seems to work all right.  
Did the instuctions have you add the higher res line in xorg.conf, or does it expect the config package to set it all up?

---

