---
title: "GDM just loads a black screen - Jaunty"
date: 2009-05-21
forum: Desktop Environments
---

### Post by dazman19 on 2009-05-21
Hi,

I was installing Nvidia drivers (brand new ones) I think somehow my gdm has broken.

Whenever it loads GDM the screen goes black and nothing happens. I cant do anything, I cant even switch runlevels (CTRL+ALT+F*)

I have tried:

dkpg-reconfigure gdm

with no luck.

I have also tried to re-install the nvidia driver, but i can only get into recovery mode runlevel 1. And it says i need to be in runlevel3 for it to work properly. although i have installed the driver ignoring this message aswell.
If i jump to runlevel 3 in recovery mode it tries to load up GDM and i have no choice but to reboot.

Any ideas?

update: 

I managed to get this to start up in low graphics mode.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):  that there is a supported NVIDIA GPU in this system, and that the NVIDIA device files have been created properly. Please consult the NVIDIA README for details.

So maybe i need to reconfigure the NVIDIA device files. I wouldnt have a clue on how to do this. And i dont know where this readme file is.

---

### Post by dazman19 on 2009-05-23
Any ideas? 

I notice that the /dev/nvidia does not exist after i have booted. 

So thats probably my problem. But i dont know why the system cant find my nvidia card. 

I ASSUME that everything that exists in /dev/ is put there once the system has ran some demon to see what devices are available for it to use as a part of the boot process.

If this doesnt exist does anyone know what i can do to get it to re-detect this device?

--EDIT--

Ok this issue is fixed. I finally managed to somehow xfix gdm for like the 5th time and this time it actually worked. Then i got into X in runlevel 3 (which is where i needed to be to install the nvidia driver) I went in and purposely UNINSTALLED the crusty driver ubuntu that stuffed the machine up in the first place, then dropped out to runlevel 3. Killed GDM then reinstalled the NVIDIA driver pkg 180.51 compile it for my kernel and restart gdm, re-edit my xorg.conf back to the settings that I like..... and reboot and I am sweet again. :D

SO IF U GOT A GF8600GTS and you use the nasty SYSTEM > ADMINISTRATION > HARDWARE drivers to install your gfx card and it gives you the error I got, this is what u do to fix it.

---

