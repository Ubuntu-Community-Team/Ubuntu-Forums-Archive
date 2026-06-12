---
title: "System freezes before login screen after upgrade to 8.10"
date: 2008-11-09
forum: Desktop Environments
---

### Post by takvera on 2008-11-09
On a basic machine I just installed Hardy 8.04 and had it running well. I went through the upgrade process to 8.10 with no problems until rebooting. When the xserver booted I get the wallpaper and then there is a colour change to a lighter wallpaper and the clock icon stops animating - the system freezes. No logon options whatsoever. Can't get into terminal mode. Everything is frozen (and I have timed this for 20 minutes before doing a manual reboot)

I have gone into the recovery menu and removed compiz and compiz-core, but there is no change from the above with the system freezing.

The machine is fairly basic:
512MB RAM
AMD Sempron 2600 processor
MSI 7181 motherboard using the onboard graphics
260GB HD

I am at a loss as to what to do next, other than reinstalling 8.04 from scratch again. Any ideas?

Further info:
Using the Intrepid LiveCD produces the same problem: system freeze just before login screen is displayed. No problem when using Hardy LiveCD.

---

### Post by aged hippy on 2008-11-09
If you want KDE 4, why not install Intrepid, rather than Hardy, upgrades often end with a broken system requiring a re-install.... in my experience.... :(

Or - if you have room - you could install both Hardy _and_ Intrepid, until KDE 4 is finished being polished up :) ... it does have a few glitches, at the moment...

---

### Post by takvera on 2008-11-09
> **aged hippy said:**
> If you want KDE 4, why not install Intrepid, rather than Hardy, upgrades often end with a broken system requiring a re-install.... in my experience.... :(

This is the first problem I have encountered out of 5 upgrades to Intrepid, so my experience is that upgrades usually work. Any other USEFUL ideas?

---

### Post by aged hippy on 2008-11-09
> **takvera said:**
> This is the first problem I have encountered out of 5 upgrades to Intrepid, so my experience is that upgrades usually work. Any other USEFUL ideas?

No. :)

---

### Post by minisori on 2008-11-09
I have at times similar problems in the laptop, but i can't find a simple error in the logs :S. At first was due to the usplash but that was fixed.

The only thing i have noticed is that booting in recovery mode and then resume, does start it properly when i have this problem.

If i don't remember bad, the bug was around launchpad some weeks ago.

---

### Post by takvera on 2008-11-10
As no-one has put forward a fix, it Looks like I reinstall 8.04 Hardy. 
mmmmm

---

### Post by km_2_GO on 2008-11-11
I'm having the same problem, also have a Sempron 2600 and 512 MB of RAM. I 'upgraded' to 8.10 from 8.04, which worked fine. Booting Live Xubuntu 8.10 and Ubuntu 8.10 had the same effect. 

I removed Compiz and searched around for other ideas, but no one seems to have any at the moment... I sure wished I had backed up my home folder. I'm able to move files via the command prompt to a USB thumb drive, but it's slow going...

I'll be reinstalling 8.04 and hoping someone comes with an answer.

Andy

---

