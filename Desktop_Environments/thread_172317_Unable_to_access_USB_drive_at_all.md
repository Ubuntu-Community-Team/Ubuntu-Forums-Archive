---
title: "Unable to access USB drive at all?"
date: 2006-05-08
forum: Desktop Environments
---

### Post by pfctdayelise on 2006-05-08
Hello,

I recently installed Breezy Badger on my NEC VERSA S940 notebook, dual-boot with Win XP, 2 USB drives/ports (?) that recognise fine in Windows, but when I plug in my flash stick in Ubuntu... no dice. Am I supposed to do something else, run something? I assumed it would be automatic but maybe it's not...

I can't even find search properly to find help about this issue, I keep getting pages about booting from USB drives. Argh. Any tips for this Linux n00b would be much appreciated.

Thanks...

---

### Post by matthewstory on 2006-05-08
You'll have to make an entry for it in the fstab file /etc/fstab if you need more specific advice I have an fstab that works with USB drives, but its on my home computer.

---

### Post by matthewstory on 2006-05-08
sorry forgot something. . . if there is an entry for it in the fstab, or after you put one in for it, you'll have to run the mount command:

prompt:# mount /dev/FLASHDRIVE

and before unplugging it you should run the unmount command:

propt:# umount /dev/FLASHDRIVE

---

### Post by brandon moore on 2006-05-09
the only way i've found to successfully solve this is to to a modprobe dump before inserting the first usb device.  here's the command:

> sudo modprobe -r ehci_hcd

i've found that my usb printer and usb camera work fine without running this command, but my usb dvd-rw, flash drive, and external hard drive don't work until i run this.  running it once works fine for an entire session.

---

