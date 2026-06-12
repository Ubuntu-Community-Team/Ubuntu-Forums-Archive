---
title: "Reboot and select proper boot device"
date: 2016-05-28
forum: Desktop Environments
---

### Post by DpinkyandDbrain on 2016-05-28
All,

 I know this might have been put on here a few times but this could or could not be different. I've installed ubuntu, fedora, centos all with the same problem while trying to boot into an OS. The problem is "Reboot and select proper boot device or insert boot media...". I've checked my bios set up and I only have one SSD installed no other media to be boot from except if I insert a CD/DVD or a usb. 

When I install the install process gives me an option to install with UEFI, saying something to the effect of... the machine has started the install process in UEFI mode but there is already a BIOS install select no to install in bios compatibility mode. No matter which one I select while installing I still get the subject line error.

Thinking my MBR was completely screwed up I tried using parted magic to erase the SSD and start from new. When I tried to boot parted magic in a live CD I get this.. VFS cannot open root device (0,0). 

So long story short I'm completely out of ideas. I'm thinking of just buying a new SSD but I feel this is a waste and/or I could be installing wrong on the computer I am using as a server. The machine is gateway DX4870, yes I know its not a very powerful machine but it'll get the job done for a home computer. 

Any suggestions will be greatly appreciated!

-DpDb

---

### Post by oldfred on 2016-05-28
With new UEFI hardware there are three ways to boot hard drive. UEFI with Secure boot on, UEFI and CSM.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

The same three ways exist for booting install media, and how you boot install media is then how it installs.
Although most systems with Secure boot on, will only boot flash drive with Secure boot, but may need specific permission to boot USB or DVD settings.

Or you can install from flash drive in one mode, but system is booting in a different mode that is not compatible. Always boot in same mode.
Both Windows & Ubuntu install UEFI or BIOS in the same mode UEFI or BIOS that you boot installer.

And if only Ubuntu best to use gpt partitioning.
But Windows only boots in UEFI mode from gpt partitioning. And only boots in BIOS mode from MBR partitioning.
So generally partitioning type gpt or MBR, goes with boot type BIOS or UEFI.
But Ubuntu can boot from gpt with either UEFI or BIOS.

I believe Gateway is based on Acer. And Acer is about the only UEFI that has specific requirement of  setting a UEFI password, and then setting "trust" on the grub/shim .efi boot files. Not sure if your UEFI has that or not.

      
 Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)
 InsydeH20 setup utility
Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)

---

