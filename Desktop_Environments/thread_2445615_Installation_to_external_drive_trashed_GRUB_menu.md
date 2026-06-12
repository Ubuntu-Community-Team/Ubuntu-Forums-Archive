---
title: "Installation to external drive trashed GRUB menu"
date: 2020-06-17
forum: Desktop Environments
---

### Post by Geoff_Lane on 2020-06-17
My main machine is a Toshiba Satellite laptop and Ubuntu 18:04 is my main system.  It has multiple boot with Windoz10 (supplied with machine) and Fedora KDE, all of which boot fine.

Within the /etc/grub.d/ folder I have a few manual entries in 40_custom for an external disk I use to experiment with alternative OSs. eg Arch, Debian and Raspberry Pi on PC.  **All work fine**.

Recently I installed Ubunu-mate onto this same external disk, checked the image with sha256sum.  Elected to install GRUB to the external disk, **always check with lsblk to verify disk** 

On reboot my grub menu on my laptop gone, displays shows GRUB prompt, if I boot to the external drive again no GRUB menu but this time GRUB-RESCUE prompt.

Fortunately I can manually boot from main grub prompts, reinstalled then updated grub so original menu back.

Why would an apparently successful installation trash the grub menu on two separate disks?

Geoff

---

### Post by sudodus on 2020-06-17
- In UEFI mode the Ubuntu installer writes the bootloader to the first drive (usually an internal drive). This is independent of what you select at the bottom of the 'Something else' window. 

- In BIOS mode you can control where to install the bootloader.

So I guess that your computer boots in UEFI mode.

-o-

In order to get things correct you should unplug, disconnect or otherwise disable the internal drive. Then the Ubuntu installer writes the bootloader to what is now the first drive, and it should be the external drive. (But it is important that there are no extra drives connected, that might be selected for the bootloader.)

---

### Post by Geoff_Lane on 2020-06-17
> **sudodus said:**
> - In UEFI mode the Ubuntu installer writes the bootloader to the first drive (usually an internal drive). This is independent of what you select at the bottom of the 'Something else' window. 

- In BIOS mode you can control where to install the bootloader.

So I guess that your computer boots in UEFI mode.

-o-

In order to get things correct you should unplug, disconnect or otherwise disable the internal drive. Then the Ubuntu installer writes the bootloader to what is now the first drive, and it should be the external drive. (But it is important that there are no extra drives connected, that might be selected for the bootloader.)

Thank you for prompt reply, yes it is UEFI mode, bit misleading to suggest it is installing at one location then do something completely different but having said that, if I had got a menu at all I would have realised maybe but I was left at the GRUB command prompt.

Disabling internal drive too much hassle on my laptop plus it has a pathetic BIOS.  Easier for me to update-grub.

Geoff

---

### Post by oldfred on 2020-06-17
Very old bugs
Also see work around during install in #23 & 26
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Ubuntu Installer uses wrong bootloader location for USB/sdb UEFI installs 
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457)

I always partition external drives in advance to include the ESP (or if BIOS a bios_grub using gpt). 
External drives always boot from /EFI/Boot/bootx64.efi, so you would not have an Ubuntu entry on external drives. 
And the default install with an Ubuntu entry in UEFI, often gets changed when the external drive is unplugged, depending on your UEFI.

---

### Post by Geoff_Lane on 2020-06-17
> **oldfred said:**
> 

I always partition external drives in advance to include the ESP (or if BIOS a bios_grub using gpt). 
External drives always boot from /EFI/Boot/bootx64.efi, so you would not have an Ubuntu entry on external drives. 
And the default install with an Ubuntu entry in UEFI, often gets changed when the external drive is unplugged, depending on your UEFI.

This is quite confusing, my external drive currently has numerous partitions with various distros all working fine though none Ubuntu on external.

I try to keep the grub menu neat on my internal drive so have manual entries for booting, I've definitely had a grub menu installed on my external drive and they've all been UEFI, no legacy BIOS.

My Ubuntu-mate installation won't boot anyway, keeps dropping me at a busybox command prompt.

Geoff

---

### Post by oldfred on 2020-06-17
Both my Debian install & Fedora install installed to sdb drive when I selected it. I really only installed those to see if grub would install to sdb.

So it only is Ubuntu's Ubiquity installer that defaults to first drive, no matter what you say.

Grub install to sdb or external does install a copy of grub as /EFI/Boot/bootx64.efi. Not sure how other installs work for sure. My Debian from a year or two ago, did not look like it had a separate grub.cfg in ESP to load grub.cfg in the install, like Ubuntu. Must have settings imbedded in the .efi boot file.

I have multiple Ubuntu installs, some now obsolete, but not yet overwritten. So I always turn off os-prober and add only the entries I want into 40_custom. 

I am now converting to use labels:
[https://askubuntu.com/questions/344125/how-to-add-a-grub2-menu-entry-for-booting-installed-ubuntu-on-a-usb-drive/344359#344359](https://askubuntu.com/questions/344125/how-to-add-a-grub2-menu-entry-for-booting-installed-ubuntu-on-a-usb-drive/344359#344359)
[https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config](https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config)
[https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835](https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835)

---

### Post by Geoff_Lane on 2020-06-19
I have a number of 40_custom entries, all of which work fine except the latest Ubuntu-mate installation, keeps dumping me at a busybox prompt.

Strangely, if I removed execute privileges from  30_os-prober I lost my menu completely but removing execute privileges from 10_linux seems to work OK for me.

Geoff

---

### Post by Geoff_Lane on 2020-06-19
[LIST]
[*][[IMG]https://ubuntuforums.org/images/ubuntu-VB4/misc/navbit-home.png[/IMG]]("https://ubuntuforums.org/index.php")
[*]oldfred
[/LIST]
 	 
       	 	 		 			 				[h=1][COLOR=#C61919]**oldfred**[/COLOR] 						[IMG]https://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-offline.png[/IMG][/h]

I have a number of 40_custom entries, all of which work fine except the latest Ubuntu-mate installation, keeps dumping me at a busybox prompt.

Strangely, if I removed execute privileges from  30_os-prober I lost my menu completely but removing execute privileges from 10_linux seems to work OK for me.

Geoff

---

