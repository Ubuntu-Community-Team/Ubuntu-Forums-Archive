---
title: "login screen showing green stripes :("
date: 2009-07-06
forum: Desktop Environments
---

### Post by jtc611 on 2009-07-06
I recently switched from vista to ubuntu.  I spend about 4 days installing software and configuring the os to my taste, and was pretty happy with it.  However, my mistake was trying to make visual effects work.  Long story short, I can only boot to the terminal (recovery mode) and cannot log in to the desktop. Here's what I did. 

1.  installed ati hardware drivers from the hardware drivers menu.  the 'display preferences' program froze up
2.  tried installing new version of catalyst/ati drivers from ati website, and upon reboot lost ability to log in because the screen shows nothing but a pair of green blobs made of stripes that look sort of like an ubuntu logo.

I have tried replacing the xorg.conf file with every other backed up version in the /etc/X11 directory and nothing works.  I am under a hard deadline coming up this Friday and am starting to regret switching to linux.  Any help is greatly appreciated.

---

### Post by GuruMadMat on 2009-07-19
> **jtc611 said:**
> I recently switched from vista to ubuntu.  I spend about 4 days installing software and configuring the os to my taste, and was pretty happy with it.  However, my mistake was trying to make visual effects work.  Long story short, I can only boot to the terminal (recovery mode) and cannot log in to the desktop. Here's what I did. 

1.  installed ati hardware drivers from the hardware drivers menu.  the 'display preferences' program froze up
2.  tried installing new version of catalyst/ati drivers from ati website, and upon reboot lost ability to log in because the screen shows nothing but a pair of green blobs made of stripes that look sort of like an ubuntu logo.

I have tried replacing the xorg.conf file with every other backed up version in the /etc/X11 directory and nothing works.  I am under a hard deadline coming up this Friday and am starting to regret switching to linux.  Any help is greatly appreciated.


I have had the same problem.

I removed the ati drivers:

go to recover mode and enter root shell

```

cd /usr/share/ati/
sh ./fglrx-uninstall.sh

```

this removes your installed drivers and you should be able to login again.



But i have a problem of my own.
I'd like to have dual screen enabled
I use ubuntu 9.04 and I have a Radeon 9800 Pro
Compiz fusion is working on one screen but when i install the drivers from ati I get the same situation as mentioned above.

Can someone help me in the right way of enabling tv-out?

---

### Post by stone@bruti on 2009-07-20
Sounds like the same problem that I had a little while back after installing the ATI closed Drivers from ATI.com.

after a bit of fiddling around. I found that I could startx from the recovery console and that the problem was GDM. I installed XDM (aptitude install xdm) and I was able to login to my desktop.

The only problem is that I can no longer use the switch user and other nifty user settings since they are only compatible with GDM.

Haven't had time to fiddle around with it lately and I probably won't have a lot of time to get back on to this forum soon. Try at your own risk since I can't guarantee that I'll be back in time to give a helping hand if things go wrong.

for the 9800 problem. I'm not sure that the actual drivers are compatible. ATI decided not to support older graphic cards with the latest releace. the problem is that since 9.04, Xorg has been upgraded so the old drivers don't work on it. So either use 9.04 with the open source drivers, use an older version of ubuntu or change graphics card.

good luck

Stone

---

