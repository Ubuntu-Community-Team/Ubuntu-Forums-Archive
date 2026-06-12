---
title: "[Lucid] Resume (STR) leaves a black screen"
date: 2010-05-10
forum: Desktop Environments
---

### Post by produnis on 2010-05-10
Hi folks,
I am running a fresh install of Lucid Lynx on my PC. 
The board is an ASRock N68-S (AM2) with an AMD SAM3 Sempron 2700Mhz CPU.
On board, there is a GeForce 7025 graphic card with nForce 630a chip.

I installed the latest nvidia-driver via jockey.

The PC suspends to RAM without problems. Via wake-on-lan, I am able to wake him up again. It is no problem to connect to the PC via ssh or even VNC after he resumes.

But the "original" Monitor, which is connected to the PC, just gives me a black screen after resume. There is no chance to bring the screen back.

So, does anyone know what I need to configure to have monitor enabled after resume?

My xorg.conf looks like this (I don't know if xorg.conf is still needed in Lucid)
> Section "Device"
Identifier "VNC Device"
Driver "vesa"
EndSection

Section "Screen"
Identifier "VNC Screen"
Device "VNC Device"
Monitor "VNC Monitor"
SubSection "Display"
Modes "1024x768"
EndSubSection
EndSection

Section "Monitor"
Identifier "VNC Monitor"
HorizSync 30-70
VertRefresh 50-75
EndSection



---

### Post by produnis on 2010-05-11
bump

---

### Post by coffeeandlinux on 2010-05-11
I am having the exact same problem! 

I am running Dell Precision 530 with Nvidia Geforce 2 GTS. 

I have completely reinstalled the Nvidia driver twice, and I did a complete fresh install of 10.04. I still have the same problem of when I wake the computer out of Hibernation or Suspend I get a black screen.

If anyone knows a solution it would be much appreciated.

---

### Post by pmos69 on 2010-05-12
File a bug or mark a current one as affecting you.
Here's one I filed about resume: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568711](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568711)

---

### Post by nerdy_kid on 2010-05-31
anyone try hitting ctrl alt f8 after?  cause my machine does that now and then, i have to manually switch vts

{edit} just read that bug, sorry

---

