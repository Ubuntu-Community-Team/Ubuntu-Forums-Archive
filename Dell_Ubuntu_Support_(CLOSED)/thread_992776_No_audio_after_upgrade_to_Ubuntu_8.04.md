---
title: "No audio after upgrade to Ubuntu 8.04"
date: 2008-11-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by vmonsanto on 2008-11-25
All sounds just disappear, and when try to open the Volume Control I get this warning:

No volume control GStreamer plugins and/or devises found.

---

### Post by Bucky Ball on 2008-11-25
Open System->Administration->Synaptics Package Manager and search for:

ubuntu-restricted-extras

Install and try again.

---

### Post by vmonsanto on 2008-11-25
That didn't solve the problem.

I've been looking around and found this. It may have the answer to my problem, but I don't understad a word.

**Upgrading from Ubuntu 7.10 to 8.04**

Remove old modem driver for Ubuntu 7.10:

$ sudo dpkg -r hsfmodem

Remove linux-backports-modules package for kernel 2.6.22-14-generic:

$ sudo dpkg -r linux-backports-modules-2.6.22-14-generic

Restore name of sound driver that old modem driver renamed:

$ cd /lib/modules/`uname -r`/ubuntu/sound/alsa-driver/pci/hda
$ sudo mv snd-hda-intel.ko.REPLACEDBYhsfmodem snd-hda-intel.ko

Remove old sound drivers from kernel module directory:

$ cd /lib/modules/`uname -r`/updates
$ sudo rm snd-hda-intel.ko
$ sudo rm snd-hda-codec.ko

Rebuild initrd and reboot:

$ sudo depmod -a
$ sudo update-initramfs -u
$ sudo reboot

If you want to install the new modem driver for Ubuntu 8.04, see here .

**If already running Ubuntu 8.04 and upgrading to kernel 2.6.24-17-generic**

Restore name of sound driver that old modem driver renamed:

$ cd /lib/modules/2.6.24-17-generic/ubuntu/sound/alsa-driver/pci/hda
$ sudo mv snd-hda-intel.ko.REPLACEDBYhsfmodem snd-hda-intel.ko

Remove old sound drivers from kernel module directory:

$ cd /lib/modules/2.6.24-17-generic/updates
$ sudo rm snd-hda-intel.ko
$ sudo rm snd-hda-codec.ko

Rebuild initrd and reboot:

$ sudo depmod -a
$ sudo update-initramfs -u
$ sudo reboot

The modem should now be recognized and fully functional.

---

