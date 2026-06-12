---
title: "constant freezing in xfce, kde, gnome, even x!"
date: 2009-02-10
forum: General Help
---

### Post by tmoneygetpaid on 2009-02-10
I've been trying to setup an ubuntu/ xubuntu/ kubuntu installation for a while now. Every time I install (have tried re-installing a couple times now), I hit the splash screen, then login, and moments after the desktop appears, everything freezes. I've tried booting to recovery mode, and even a terminal freezes. I've booted from cd and tried updating-upgrading packages and afterwards, same behavior. Tried reconfiguring xorg.conf. I've tried installing kubuntu and xubuntu 8.04 via -desktop package install, and installing ubuntu 8.04 and 8.10 from cd.

Any ideas?

My system is a MSI 975X Motherboard, Radeon x1650pro video card, core 2 duo e6600, two sata hard drives.

Help!

---

### Post by tmoneygetpaid on 2009-02-11
help

---

### Post by tmoneygetpaid on 2009-02-12
tried purging all compiz packages, too. still no dice. ran memtest. ran video card diagnostic. nothing.

---

### Post by LowSky on 2009-02-12
have you tried the alternative Cd install?

seems odd it just keeps freezing

can you boot into recovery mode?

Does it happen on a fresh install?

---

### Post by tmoneygetpaid on 2009-02-13
Thanks for your response. Yeah, all my installs have been with Alt. CDs. I can almost never get an installation on any hardware to go through with a GUI installation.

I can boot into recovery mode, and when I hit a terminal it'll still freeze after a minute.

And yes, it happens on a fresh install, too. I've tried deleting the partition, then installing from scratch. At this point, I've done maybe 4-5 fresh installs.

---

### Post by Bonsanto on 2009-02-14
Same problem here! :(

---

### Post by razy60 on 2009-02-15
If it is at all possible try to boot into safe graphical mode F4 on the boot screen of the cd. If you are successful then you may have graphics card issue, 
Are you trying to use 64bit or 32bit system if its 64 then try 32(there have been probs with64)
run the memory check and the cd check from the cd bootup screen to ensure there are no problems with them.

Raz

Edit: also if you get into ubuntu in safe graphical mode then you could try to reformat the drive unless you are dual booting in which case just do the partition you want to use.(clean out any old junk you may have left from previous attempts)
Disconnect the drive you are not using(only do this if you are comfortable with the idea of opening up your pc)

---

### Post by tmoneygetpaid on 2009-02-17
I have tried both 32-bit and 64-bit 8.04, and I think only 64-bit 8.10.

Booting into safe graphics mode on the GUI install CD crashed me as well.

I've run memtest through one full pass (which takes a whole lot longer than it does for me to boot into Ubuntu and get a crash), so I think mem is fine. I have done the CD test, too.

I bought a new video card that I'll be installing later. I'll see if that fixes this.

---

### Post by tmoneygetpaid on 2009-02-18
Nope. Bought a brand new HD4830 vid card, installed, booted to Ubuntu and got about 2 minutes before freeze.

Help!

---

### Post by tmoneygetpaid on 2009-02-24
Please help. Really want to get off of Windows.

---

### Post by tmoneygetpaid on 2009-03-05
Fixed: apparently it was being caused by running 1440x900 resolution on my video cards. switched down to a non-widescreen and it seems fine.

---

