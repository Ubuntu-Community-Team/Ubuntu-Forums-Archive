---
title: "GDM - Black Screen"
date: 2007-05-04
forum: Desktop Environments
---

### Post by philldo on 2007-05-04
Hi,

I recently installed gnome-splashscreen-manager, and it installed fine, however, when i logged out and logged back in i can no longer load GDM.

X and gnome still work perfectly, however i cannot actually load GDM to get to the login screen....

I have temporarily installed kdm so i can get to the login screen, and then login to gnome.

What happens when it boots, is the ubuntu circle (cursor) just goes around and around infront of a black screen, and nothing becomes of it.

I cannot find out what has caused the problem and/or any errors in any logs..

It is a newly install of fiesty, 2 weeks old if that...

Can anyone shed some light please?

Thanks :-)

---

### Post by flathampster on 2007-05-23
I have exactly the same problem. Does anyone have a solution yet ?

If I boot in recovery mode I can then type startx and it boots into roots desktop. 

I did an upgrade from Edgy to Fiesty using the upgrade button. It took about 6 hours to upgrade over the internet and rebooted. Everything else appears fine, but the greeter just wont load. I tried to apt-get install GDM and apt-get upgrade GDM.

---

### Post by Lieter on 2007-05-23
does ```
dpkg-reconfigure gdm
``` help?

---

### Post by flathampster on 2007-05-23
Thanks for the suggestion, I did this and it returned...

* Reloading GNOME Display Manager configuration...
* Changes will take effect when all current X sessions have ended.
invoke-rc.d: initscript gdm, action "reload" failed.

I rebooted the PC and it still has the same sypmtoms

---

### Post by bjornhakon on 2007-05-24
Sounds like the same problem I had. Have a look at this thread : [http://ubuntuforums.org/showthread.php?p=2702403]("http://ubuntuforums.org/showthread.php?p=2702403") , maybe that can help

---

### Post by flathampster on 2007-05-25
Thanks, yes I have since read your thread and i followed all those instructions.

It seemed to work the same way. I was able to stop and start gdm and get the login preferences window open, although as soon as I tried to do that it required gdm to be running. If I then started GDM it would keep throwing up the black screen.

After a reboot it was unfortunately exactly the same.

I managed to apt-get remove gdm  then apt-get install gdm, but the result was the same again.

I then did "apt-get remove gdm" followed by "apt-get install kdm"

It works now but the login screen is for Kubuntu, then it loads normally. To be honest Im not sure what I accomplished with this fix.

---

### Post by bjornhakon on 2007-05-25
Yeah, I know - it's quite tedious. For about every little change or mouseclick you make, the blackscreen will come back, but just keep pressing ALT+CTRL+F7when that happens, and you will get back to the X-session where you are logged in. With some patience, I managaed to make the necessary changes (read: undo the stupid changes I made before ;) ) and when I booted up again, the loginscreen was normal. Then I was able to set up the loginscreen the way I wanted it (or almost - I settled for the default Human theme instead of the one I tried to use  ;) ). Now everything works just fine.

I learnt one thing, though,  from this: Make one change at a time. That way I will know exactly where the problem is. In my case, was the problem with the loginscreen or with the automatic / timed login combination? I don't know, but if I care to, I can always find out. I'll just make the same changes again -but one at a time ...

Bjorn Hakon

---

### Post by fluxe on 2007-05-28
I just wresled with the GDM black screen problem.  Originally I was able to CTRL-ALT-F1 to switch to tty1, and there sudo /etc/init.d/gdm stop.  Then startx would start xorg.  I'm not sure how but I was able to destroy that situation promptly so that a black screen came up upon "startx" too.  I must have done something stupid.

Anyway, I just solved both problems in an embarrassingly simple way.  I went to /etc/X11 and copied xorg.conf.backup (from a while ago) to xorg.conf.  After that GDM and Xorg worked just fine!  Something in upgrading from Edgy to Feisty must have confused X.

Trying to analyze the diff between the two config files, the most suprising thing is that the HorizSync values were different.  Namely the value went from "28-80" in the good backup version to "28-51" in the new bad version.

Maybe the upgrade to Feisty doesn't rebuild the xorg.conf correctly.  It might be worthwhile to see what's been happening with xorg.conf in /etc/X11.

---

### Post by tekniche on 2008-05-14
> **Lieter said:**
> does ```
dpkg-reconfigure gdm
``` help?

I am having the same problem. This command looks like it will solve my problem though. I have tried multiple times to stopx startx gdm stop gdm start with no luck. i will try this command.

---

### Post by tekniche on 2008-05-14
Holy crap! Okay, so I am trying to install the nvidia drivers for my video card. When I got home today I was able to reconfigure gdm , reconfigure the x server, and reinstall my video card driver. I got past the black screen where the gdm would not load and was able to login through the gui. When I log in my screen is pushed over to the left about a quarter of an inch. I am not sure how to fix this. Autoconfiged the monitor, power cycled monitor went through the whole reinstallation of the driver and i got nothin. Any help would be greatly appreciated. Thanks!

---

