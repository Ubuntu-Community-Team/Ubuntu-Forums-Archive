---
title: "blank screen after login"
date: 2007-08-12
forum: Desktop Effects &amp; Customization
---

### Post by Corbin on 2007-08-12
Hey, ive been trying to mess around with compiz-fusion and other graphic effects settings/drivers and all that good stuff. and its hard to tell what exactly  caused the problem. Because i installed/changed soo much stuff.

But basically the problem I'm having; is that i boot Ubuntu and the login screen popes up. So i log in and it loads a silo wet of the top and  bottom bars to then just coming up with a blank white screen with my cursor. I am able to move the cursor around and what not but if i do alt+tab then it does as it usually does and bring sup the 3 boxes i had left open gaim and two folders. So it shows the little logos in the bottom of each box area but its ALL white.... 

(so its running in the background. just has no means of displaying it correctly...) 

Any help would be sweet.

Also my second questions is.
Am i able to set a restore point (kinda like crapdows) so as I'm messing around getting everything all set up correctly i can just revert back ifi ever mess somthign up agaoin?


-Thanks again 


(I am running the newest version of Ubunto . with a 32 bit P4)



Edit:Also if i guess around clicking and get it to restart. It will flash my desktop ( no icons, just wall paper and the task bar outlines) and then continue to restart.

---

### Post by ddrichardson on 2007-08-12
Yes, make a backup of Xorg.conf.
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

You can retore it if you have any login problems. But in this case it sounds more like something is loading but not handing over in your session. I'm sure someone with more Gnome experience will explain how to backup Gnome settings.

---

### Post by Corbin on 2007-08-12
Yea, i know about copying the xorg.conf file (ive had to restore it several times). Ive just been restoring it of my thumb drive. (but backing up the xorg.conf file isnt a system restore tho) *right......?*

and yea it does sound like something it loading but just not either compatible or wrong settings

-Thanks

---

### Post by ddrichardson on 2007-08-12
There are plenty of ways to backup - from imaging to incremental, have a look in Synaptic. You could just backup up your entire home folder using tar if you want to keep it simple.

---

### Post by Corbin on 2007-08-12
ahh, Thanks for the backing up ideas/sugjestions


and i got it (KINDA) 

I just did 
sudo apt-get --purge remove compiz*

and that just got rid of all my effects and now i just have to go through and re download them and work through the settings slowly.

-Thanks

---

