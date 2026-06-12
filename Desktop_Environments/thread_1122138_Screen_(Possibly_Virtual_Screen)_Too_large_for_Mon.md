---
title: "Screen (Possibly Virtual Screen) Too large for Monitor"
date: 2009-04-10
forum: Desktop Environments
---

### Post by ryanjones102 on 2009-04-10
Hi all,

I've scanned the forums, and haven't been able to find anything appropriate.

I just installed Ubuntu 8.10 onto an ex-Windows XP laptop. Under XP, i was running a screen resolution of 1280 x 1024 - it worked fine. Since installing ubuntu, it has selected 1600 x 1200 as a resolution for me, which works to a degree, in that I can see most of the screen. Only problem is, a considerable chunk of the desktop (bottom and right) is missing...I've tried to change screen resolutions thru the GUI, no joy it just does that crazy thing where you can't see anything on the screen and it's all lines. After 5 or 6 re-installs to get going again, i'm in the same situation. 

Has anyone seen anything like this before? 

I'd appreciate your thoughts or ideas of how to fix this?

Thanks in advance,

Ryan

---

### Post by rolando on 2009-04-10
What type of graphics card do you have?

---

### Post by ryanjones102 on 2009-04-10
Thanks for your reply.

I have everyone's fave, the Video VIA S3G Unichrome Pro IGP! As standard in any bottom end laptop. 

I've tried the Unichrome project on sourceforge, but didn't have too much fun with that!

---

### Post by rolando on 2009-04-10
Mmm, not your stock ATI, Nvidia or Intel.

How confident are you in posting me your xorg.conf file?

If you go to terminal > type sudo nautilus

Then go > File system > etc > X11 > and open xorg.conf

Then cut and past the contents of the file in a new post here.

After that you can look at changing the resolution in the xorg.conf, but you may bork it but not all is lost.

If you do make any changes make sure you back up the old file before logging in and out again.

If you do bork it then you will have to use the terminal and rename the xorg.conf to xorg.conf.old and rename the backed up on to xorg.conf

I have lost count the number of times I have ruined xorg.conf trying to tweak it, getting my tablet laptop to work etc etc

---

### Post by rolando on 2009-04-10
Another thing I just found is this in Synaptic

X.Org X server -- VIA display driver
OpenChrome is a project for the development of free and open-source drivers
for the VIA UniChrome video chipsets.

Have you got xserver-xorg-video-openchrome installed??

What version of Ubuntu are you using??

---

