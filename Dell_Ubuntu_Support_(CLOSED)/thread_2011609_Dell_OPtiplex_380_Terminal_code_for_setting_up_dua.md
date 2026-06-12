---
title: "Dell OPtiplex 380: Terminal code for setting up dual HDD/OS"
date: 2012-06-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Smithie on 2012-06-27
So, I'm picking up a new-to-me Dell Optiplex 380.  The specs are:

Pentium Dual Core E5800 3.20 GHz
4.00 GB Ram
Windows 7 32bit
250GB HDD
Optical Drive

I plan on moving my nVidia video card and my current HDD with Ubuntu already installed into the new unit.  I plan to master the Ubuntu HDD and then slave the smaller Windows 7 HDD.  I'd like the dual boot option to show up on start, so either OS could be chosen.

But...I have no idea what code to set up to do this.  So, couple of questions:

1 - Do I need to run a repair out of terminal when I install the Ubuntu HDD so it recognizes the new computer and loads the correct packages appropriately?  Or, should I just do a fresh install?

1a - If fresh install is recommended, what is the best functioning release on this system?  Ubuntu 12.04?  Mint 13?  Am I right I should stick to 32-bit?

2-  What terminal commands/code do I use to set up the dual boot option at start up, with the Ubuntu acting as master?

I realize there is some information out their about this, but, since I'd prefer to avoid the fresh install and just use the old Ubuntu HDD as is, I wanted to make sure on the coding end of things.

Thanks!

---

### Post by DELL JonathanS on 2012-06-28
I would start by taking a look at Boot-Repair: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) and hopefully you would not have to use any terminal commands!
 
I would also like to offer some perspective for your consideration: Since Windows is already installed and working correctly, I think you will probably have the easiest time leaving it there rather than making it the slave disk. Ubuntu does not care which disk it is on (though an existing installation may). Unless you have a special reason it will most likely be easier to use the Windows bootloader with these instructions for example: [http://askubuntu.com/questions/62440/is-it-possible-to-boot-ubuntu-using-the-windows-bootloader/62442#62442](http://askubuntu.com/questions/62440/is-it-possible-to-boot-ubuntu-using-the-windows-bootloader/62442#62442)
 
As far as moving the existing Ubuntu installation into the "new" system, the chipset on the OptiPlex 380 is the Intel G41 graphics/memory controller hub with the ICH7 I/O controller hub and these do have kernel support. Ubuntu will most likely be able to load the necessary modules for basic operation. If you have any static IP configurations (based on MAC address in /etc/network/interfaces) or bridges, those interfaces will not come up until you reconfigure that file to reflect the new hardware's MAC addresses. Also you will have the potential to panic at boot if the drive lettering is different and the root device is identified by device node (e.g. /dev/sda4) rather than UUID -- this is a likely scenario if the disk is currently /dev/sda in the system it came from and will become /dev/sdb in the new system (because sda is the Windows drive). You may be able to use the information in [http://manpages.ubuntu.com/manpages/dapper/man4/initrd.4.html](http://manpages.ubuntu.com/manpages/dapper/man4/initrd.4.html) to ensure you are able to find the root device and recover from recovery mode if anything goes wrong. Finally, any module customizations or blacklists on the existing install may not be suitable for the new hardware platform and may need to be reconfigured, which you can also do in a recovery shell.
 
For the simplest experience and long-term peace of mind and configuration consistency, it might actually be best to install the Ubuntu hard drive (with Windows disk still primary/boot device), and then install a fresh copy of 12.04 on the Ubuntu disk, allowing Ubuntu Setup to configure the dual-boot for you. Just take care to not overwrite the Windows drive by mistake! The Intel E5800 CPU does support the 64-bit ([http://ark.intel.com/products/42802/Intel-Pentium-Processor-E5800-%282M-Cache-3_20-GHz-800-MHz-FSB%29](http://ark.intel.com/products/42802/Intel-Pentium-Processor-E5800-%282M-Cache-3_20-GHz-800-MHz-FSB%29)) instruction set and I don't see any reason why a 64-bit OS wouldn't work on there. I'm not sure why we didn't support 64-bit Windows on the OptiPlex 380 given the hardware, so if you want to do 64-bit fresh install then I would recommend booting to the Live CD environment and making sure everything seems to work ok. The latest stable version of whichever distro you choose would be best for most available support, so for Ubuntu that would be 12.04 right now, I am not familiar with Mint though.
 
Thanks for reading down this far -- I hope it has been helpful and I did not get carried away! Let us know what you try and how it goes and if you need assistance!

---

