---
title: "Windows Distortion"
date: 2005-09-20
forum: Desktop Environments
---

### Post by Crazed on 2005-09-20
I'm brand new to linux and I'm not expeirenced with installing and setting up OS.
I installed linux through Microsoft Virtual PC.  I have gone through the installation many times trying to see if i missed a step but i'm pretty sure i haven't.  Linux loads up fine and everything, i can get into the windows and do anything i want in it fine.  The problem is that it is distorted, its completely stretched out and i can barely read anything on the screen.  Anyone know what i can do to fix it?

---

### Post by dbott67 on 2005-09-20
[QUOTE=Crazed]I'm brand new to linux and I'm not expeirenced with installing and setting up OS.
I installed linux through Microsoft Virtual PC.  I have gone through the installation many times trying to see if i missed a step but i'm pretty sure i haven't.  Linux loads up fine and everything, i can get into the windows and do anything i want in it fine.  The problem is that it is distorted, its completely stretched out and i can barely read anything on the screen.  Anyone know what i can do to fix it?[/QUOTE]

I've had similar issues using VMware and some linux distros.  From what I've gathered about the problem (at least in VMware) is that the xorg.conf file is using the wrong video driver.

Try the following:

1. Download the "LiveCD" version of Ubuntu & burn it to CD.
2. Setup a new VM in MS VPC and boot from the live CD.  I've found that the live CD tend to pick the correct video settings and everything looks great.
3. If the system boots up correctly, copy the xorg.conf file to a floppy or USB device.
4. Boot into your installed version of linux and copy over the xorg.conf file.

Good luck,
Dave

---

