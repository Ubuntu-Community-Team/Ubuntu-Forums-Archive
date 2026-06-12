---
title: "Help with Installation"
date: 2005-05-07
forum: Desktop Environments
---

### Post by Andre N. on 2005-05-07
For some strange reason, I can't seem to install Kubuntu. After I press enter at the boot screen, all this gray text pops up. After a couple of seconds (about half a minute), it freezes. It just stops right there. The last message I see is  "Attached scsi removable device sda at sci1, channel 0 , id 0 , lun 0"  The same thing happens on the Live cd as well. I have tried many times already. Please help.

---

### Post by mtron on 2005-05-07
First of all: welcome to ubuntu! 

Please give us as many information of your hardware as possible. If you are running a microsoft os go to the - i think it is called "system manager" or just system and device manager, there you will find a list of your hardware. Post the relevant information

second, take a look at [http://www.ubuntulinux.org/wiki/HardwareSupport](http://www.ubuntulinux.org/wiki/HardwareSupport) or [http://www.tldp.org/HOWTO/Hardware-HOWTO.html](http://www.tldp.org/HOWTO/Hardware-HOWTO.html) , and try to find out if your hardware is compatible with Linux. 

Are you able to run another LiveCD distro like knoppix?

cheers mtron

---

### Post by Andre N. on 2005-05-07
I have a Dell Dimension 8400 with an Intel Pentium 4 3.40 GHz with HT CPU. I have a gig of RAM. I also have an ATI Radeon X300 (128 MB) and a Creative Sound Blaster Audigy ZS 2 sound card.

And yes, I am able to run other distros. I was able to run Linspire Live! very well. I think it's the ATI card that is messing it up for me.

---

### Post by mtron on 2005-05-20
sorry for the late reply.. i forgt this thread  :neutral: 

Check out the special boot options, some warty users reported similar problems.

If nothing helps, try this suggestion

    * press [F2] when the DELL logo is displayed to enter the BIOS.
    * Arrow down until you reach the "Drives" section.
    * Press the right arrow to expand the list.
    * Continue to arrow down until you reach the section "SATA Operation" and press [ENTER].
    * The default setting is "RAID AUTODETECT / AHCI". Select "RAID Autodetect / ATA" instead then press [ESC]
    * save your changes on exit and reboot. 

This should do it

---

### Post by cgreentx on 2005-09-08
I have an issue with this solution.  While setting to ATA mode allows me to install Ubunto on my Dimension 8400, it renders my Windows installation inoperable.  I could live with a re-install if that were the only caveat, but by turning off AHCI you are also completely disabling Native Command Queueing which was one of the main reasons I chose the drives that I have in this system.  It seems to me that the kernels in the latest distros should be capable of running 1.5 year old SATA chipsets in native mode... Am I wrong here?

Chris Green

---

