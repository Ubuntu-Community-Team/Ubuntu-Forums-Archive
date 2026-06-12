---
title: "GRUB - Installation nightmare"
date: 2021-07-16
forum: Desktop Environments
---

### Post by Geoff_Lane on 2021-07-16
Toshiba Satellite Laptop
Ubuntu 18:04LTS
Triple boot Ubuntu (main system, Win10 and Fedora

Ran a live Ubuntu image on a USB, went for installation onto a separate attached USB.

On setup declined install alongside current system, decilined wipe disk and fresh install went for the manual install.

Selected to install GRUB on the USB drive I was installing system to, so far easy peasy.

Installs and runs fine, device for a friend who is having Windoz problems so maybe get him over to Ubuntu.

[B]Now my problem.

[/B]Grub boot menu disappeared from laptop, presented with grub command line.

Had this numerous times before with grub, know how to boot from command line and reinstall GRUB but now, after years of being on GPT5 it is now been moved to GPT8 :mad:

How on Earth does this happen, it should not have touched my internal drive, let alone changed the partition.  My main Ubuntu OS now shows up at the end of GPARTED and I've got some small extra partitions I never created.

Checked the USB drive where Ubuntu installed to, no EFI partition and no boot menu.

Geoff

---

### Post by oldfred on 2021-07-16
Ubuntu in UEFI boot mode defaults to use first drive's ESP. Usually then the internal drive's ESP. This works if only one drive, or if second drive always booted from same system.

If installing to any second drive and particularly to any external drive best to have an ESP on that drive. 
We filed a bug report many years ago.

Posted work around to manually unmount & mount correct ESP during install #55 or( #23 & #26)
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. (I have not had that work, but others have.)
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall of grub to correct drive. 

Remove esp flag from Windows before install to second or external drive - Tim Richardson
[https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator/1056079#1056079](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator/1056079#1056079)

---

### Post by Geoff_Lane on 2021-07-18
> **oldfred said:**
> Ubuntu in UEFI boot mode defaults to use first drive's ESP. Usually then the internal drive's ESP. This works if only one drive, or if second drive always booted from same system.

If installing to any second drive and particularly to any external drive best to have an ESP on that drive. 
We filed a bug report many years ago.


You gave me some excellent guidance before when I had a similar issue with a number of Linux images in various partitions on an external drive.

I wasn't expecting this issue on a Live Image installation, would not have even commented had all my partitions remained in the same place as I am quite used to that.

Following your advice on my laptop I now use /etc/grub/d/40_custom to boot

Ended up here using mkusb for a persistent image, so much easier.

Thank you for input.

Geoff

---

