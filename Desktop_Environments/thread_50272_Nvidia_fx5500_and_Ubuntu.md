---
title: "Nvidia fx5500 and Ubuntu"
date: 2005-07-19
forum: Desktop Environments
---

### Post by JulesBurgess on 2005-07-19
I have Ubunto 5.04 Hoary, updated recently.

I have just got an Nvidia fx5500 video card, I managed to install it on Fedora fine.

On Ubuntu it will not even use it as an ordinary VGA card.

How do I get it to work.

It talks about the X files needing adjusting.
On Fedora it did it automatically.

---

### Post by JayCnrs on 2005-07-19
Does it drop you to the CLI. If it does login to Ubuntu then go to /etc/X11, then you will need to use **sudo pico xorg.conf**. Look for the section that should look something like this:

```
Section "Device"
        Identifier      "NVIDIA Corporation NV11 [GeForce2 Go]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "NvAGP"  "3"
        Option          "DigitalVibrance" "255"
EndSection
``` 

You can then change the Driver part with:

```
Driver  "nv"
``` 

This will let your gui come up, then you will want to check out the Ubuntu guide for the Nvidia drivers install.

---

### Post by clearnitesky on 2005-10-24
umm, how about this one:
I've got an FX5500 that I configured really easily on Slackware 10.0 because it had all the kernel sources in the right place. 
I've just installed a new version of Breezy Badger and it doesn't. The kernel sources I found on apt don't match my kernel (2.6.12.9) and it wont accept the pre-build nvidia drivers either, I get this message:

> Error: API mismatch: the NVIDIA kernel module is version 1.0.7174, but
this X module is version 1.0.7667. Please be sure that your kernel
module and all NVIDIA driver files have the same driver version.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):      that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):      that the NVIDIA device files have been created properly.
(EE) NVIDIA(0):      Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.


Any ideas?

---

