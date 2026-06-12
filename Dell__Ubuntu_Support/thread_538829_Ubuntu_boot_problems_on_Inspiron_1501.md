---
title: "Ubuntu boot problems on Inspiron 1501"
date: 2007-08-30
forum: Dell  Ubuntu Support
---

### Post by Senka on 2007-08-30
I'm using a Dell Inspiron 1501 and I've been trying to get Ubuntu 7.04 to install on an 80GB external hard drive (Ubuntu says it's a Fujitsu MHV2080AH). The install runs fine but when I go to boot Ubuntu that I just installed on it, Grub says "Error 17: Cannot mount selected partition." From what I understand, this error means that the partition is there but Grub can't read it. I've tried installing to this drive several times, including partitioning the drive through the install using each option as well as using cfdisk to partition the disk and then rebooting before running the install.

I have to install Grub on the external hard drive, otherwise it would cause problems with Vista. Maybe this is causing the problem? If this is the case, is there any way to fix it? Or could it be the hard drive itself causing the problem? Or am I way off the mark on guessing what's causing this?

---

### Post by pheonixind on 2007-08-30
Wow, that's a good one.  I have never tried to boot from a USB or External drive with the main OS still on the system itself.  I'll try it when i get home and see what happens.  Vista on Portable, and Ubuntu 7.04 on External, with Grub on external for booting.

---

### Post by Senka on 2007-09-07
Does anyone have any ideas on this?

---

### Post by neptho on 2007-09-07
Did you install grub into the root of the drive, or into the partition, itself?

You need to play some fancy footwork when you play with multiple disks.  Do you get any other error if you go to the boot menu in BIOS, and tell it to boot from the external disk?

---

### Post by Senka on 2007-09-07
I installed grub to the root of the drive and I get the same error when I try to boot from the boot menu in the BIOS.

---

### Post by neptho on 2007-09-07
> **Senka said:**
> I installed grub to the root of the drive and I get the same error when I try to boot from the boot menu in the BIOS.

Try booting back from the CD, then go into 'repair mode'.

Reinstall grub by entering grub, and tell it to install to the root of the disk.

If this is your second disk (and is seen), it should be considered as 'hdb' or 'sda', 'sdb', so that would look like:

```
%grub-install /dev/whatdrivename
```

If that doesn't work, you can always run 'grub', then call the installation from within:

```
%sudo grub
grub>install (hd1)
grub>quit
```

---

### Post by mrbrownct on 2008-01-18
yeah.  there is an issue here with the 1501.  i have both an xps m1210, and an inspiron 1501.  with the internal drives out of both.

out of fun and curiosity,i installed ubuntu on a usb flash memory stick and an external usb hard drive for the 1210 and it runs perfectly both ways.

i attempted the same thing on the 1501 and get "no operating system found", and i know it sees the devices and is set to boot from them.

wassup with that?

---

