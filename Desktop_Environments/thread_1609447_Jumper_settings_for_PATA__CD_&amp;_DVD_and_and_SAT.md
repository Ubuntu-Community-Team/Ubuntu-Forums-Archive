---
title: "Jumper settings for PATA  CD &amp; DVD and and SATA HDD"
date: 2010-10-30
forum: Desktop Environments
---

### Post by welshmike on 2010-10-30
My apologies if this is an inappropriate thread or forum as it does not look like a problem specific to Ubuntu.

A friend wants to dump his Windows XP system so that I can install Ubuntu 10.04.
His PC has a PATA CD R/W drive and a PATA DVD R/W drive on the only single channel. 
It has a SATA HDD.
The PC BIOS will not allow me to change the order of drives to boot from, only shows the CD R/W drive first then the SATA HDD and will only boot from the HDD.
I tried getting the PC to boot from the CD or DVD drive so that I could install Ubuntu from a live Ubuntu CD by disconnecting the power to the HDD, This did not work.
With a live Ubuntu flash drive connected the BIOS does not allow me to change the boot order to boot from the flash drive.
I was able to boot from a live Ubuntu flash drive by disconnecting the HDD power.
I then quickly hot plugged the power to the HDD so that the Ubuntu installation process could use it. But the installation of Ubuntu did not proceed, probably because it was too late to have the HDD recognised.

I suspect that the jumper settings on the CD and DVD drive are such that they are unbootable.

Does the team have any advice how I may overcome the above problem please?

---

### Post by gbestrada on 2010-10-31
I also had the same problem with my computer until I reset  the battery 
on the motherboard and it forced me to configure all the settings for the motherboard 
through the BIOS .
you may try that ,it may work for you too..    :) =  :P

---

### Post by welshmike on 2010-10-31
Thanks,

So as well as checking the jumper settings I'll disconnect the BIOS battery, reconnect it and see if I can then change the boot order.

---

