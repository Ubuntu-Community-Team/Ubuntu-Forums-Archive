---
title: "broken X after upgrade, error messages below..."
date: 2009-12-01
forum: Desktop Environments
---

### Post by brjoon1021 on 2009-12-01
Hi,
I have 9.10 ubuntu, ext4 filesystem (I have liveCDs that will mount ext4, the new Mint). My video card is a Nvidia 6600 GT
I have an MPlayer PPA in my apt sources.lst, synaptic showed an upgrade for MPlayer that I recall had some need for a new Nvidia driver, kernel or something in the [COLOR=Red]195.xx.xx series[/COLOR] - note that this is different than the boot screen lines below. I went through the upgrade and I have not been able to get into x after many reboots.

Here are the last few lines of the boot screen:

*starting kernel log daemon...
*starting MySQL database server mysqld
*Running DKMS auto installation service for kernel 2.6.31-15-generic
* nvidia ([COLOR=Red]185.18.36[/COLOR])
... done.
* starting Commun Unix Printing System: cupsd
[COLOR=Red]*[/COLOR] PulseAudio configured for per-user sessions

Ubuntu 9.10 ubuntu tty1

ubuntu login: _                     [COLOR=Red](it booted into the graphical screen before...)[/COLOR] 

- after I login and "startx" I get:

Many lines about the Xorg server, but these seem to be just information, then
(EE) Failed to load module "nvidia"  (module does not exist, 0)
(EE) No drivers available

Fatal Server error:
no screens found

- I am told that I can check the log file at "/var/log/Xorg.0.log" for additional information. then...

 ddxSigGiveUp: Closing log
giving up.
xinit: No such file or directory (errno 2): unable to conect to X server
xinit: No such process (errno 3) Server Error.

- I can't get any further.
I think that the MPlayer update brought with it a new Nvidia driver that either isn't working or can't be found by the system..

can you help

---

### Post by Greenwidth on 2009-12-01
This thread might help:
[http://ubuntuforums.org/showthread.php?t=1305459](http://ubuntuforums.org/showthread.php?t=1305459)

---

