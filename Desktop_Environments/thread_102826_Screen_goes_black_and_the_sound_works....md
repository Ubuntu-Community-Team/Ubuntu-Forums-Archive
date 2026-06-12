---
title: "Screen goes black and the sound works..."
date: 2005-12-12
forum: Desktop Environments
---

### Post by Snipersnest on 2005-12-12
What do you do when your system loads up the screen goes black and the ubuntu jingle can still be heard in the background?
 
I recently tried to install the Nvidia 8174 drivers.. I thought I removed all the old nvidia-glx stuff I must have been wrong. In the install it told me some other device or mechinism had installed drivers on the system before and that it would try to remove them.. I trusted it.. it errored out saying it it couldn't find some file ending in .ko  and then it gave some error about it..then it installed the new 8174 drivers and updated the xconfig ..
 
rebooting the screen goes black and the sound still works.. I'm not sure how to fix it or where to start.  I just want to be able to use my SLI finally in Linux.. I've been waiting on these drivers for 6 months now.
 
Can somebody give me a hand fix that and telling me the easiest way to install the nvidia chipset drivers too?
 
Ubuntu 5.10
2.6.12-10-k7-smp
Athlon 64 X2 4400+
1GB PC3200 Corsair XMS Xpert
500GB HD (WD 16mb Sata 2)
Asus A8N-SLI Premium

---

### Post by Bentu on 2005-12-12
That sounds to me like your x server is stuck, if so you should be able to kill your x server and get to a command line by holding down the alt and ctrl keys together, then pressing backspace. I believe I've read on this forum how to install video drivers, but I'll have to search for it when I have time (or you can try a search).

Ben

---

### Post by Snipersnest on 2005-12-13
I asked a buddy of mine for help and this link tells everything I did to get to this point.
 
[http://www.snipersnest.com/index.php?name=PNphpBB2&file=viewtopic&t=248]("http://www.snipersnest.com/index.php?name=PNphpBB2&file=viewtopic&t=248")

---

### Post by Snipersnest on 2005-12-14
bump....
 
I tried to reinstall the drivers but still nothing...Same results..
 
If I update the xorg.conf back to nv I get video of course... But why does X hang when starting up with nvidia?
 
Theres no errors in the logs or anything to tell me something is wrong...I don't know what else to try

---

