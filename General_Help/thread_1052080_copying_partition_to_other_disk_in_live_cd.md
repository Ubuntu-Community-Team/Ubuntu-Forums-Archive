---
title: "copying partition to other disk in live cd"
date: 2009-01-27
forum: General Help
---

### Post by djbushido on 2009-01-27
I am wanting to pretty much clone my drive to a larger drive. the only problem is that clonezilla isn't detecting the drives since they are usb. I can do this graphically via virtual machine, but for some reason my machine can't boot graphical live cd's.

Anyway, is there a way to copy the partitions out? Any help is appreciated.

---

### Post by Irony on 2009-01-27
[http://ubuntuforums.org/showthread.php?t=416710](http://ubuntuforums.org/showthread.php?t=416710)

---

### Post by djbushido on 2009-01-27
Do I also need to update /etc/fstab to reflect UUID changes?
Also, is there a way to set a UUID, such that I can reset my swap UUID? Previously repartitioning this changed UUID, and "quiet" boot mode didn't work.

EDIT: Just to let you know, this is so I can move my system to another drive.

---

### Post by caljohnsmith on 2009-01-27
> **djbushido said:**
> Do I also need to update /etc/fstab to reflect UUID changes?
Also, is there a way to set a UUID, such that I can reset my swap UUID? Previously repartitioning this changed UUID, and "quiet" boot mode didn't work.
You can transfer the original UUID of your old partitions to your new partitions if you want by doing the following (for an ext2/ext3 partition):
```
sudo tune2fs -U <original UUID> /dev/sdXY
```
And you can also transfer the UUID of the original swap partition to the new swap partition with:
```
sudo mkswap -U <original swap UUID> /dev/sdXY
```
If you just want to clone the drive though, how about instead doing this:
```
sudo apt-get install dcfldd
sudo dcfldd if=/dev/[COLOR="Blue"]<source drive>[/COLOR] of=/dev/[COLOR="Blue"]<destination drive> [/COLOR]statusinterval=10 bs=10M conv=notrunc,noerror
```
"dcfldd" is better than dd in my opinion since it will show you the progress of the copying. That's probably how I would do it.

---

### Post by djbushido on 2009-01-27
Will this also copy boot record? I would like to be able to boot this, so would need boot-record copy as well.

---

### Post by caljohnsmith on 2009-01-27
> **djbushido said:**
> Will this also copy boot record? I would like to be able to boot this, so would need boot-record copy as well.
Yes, dcfldd does a true byte-for-byte clone of your source drive, so it copies the MBR and everything. Your destination drive would of course have to be at least as large or larger than the source drive for it to work. Once you are done cloning, if you want to try and boot your newly cloned partitions on the destination drive, it would be good to first disconnect your source drive, because the UUIDs will be the same. That means if you boot the destination drive with the source drive connected, you might actually end up booting into your source drive partitions. Good luck and let me know how it goes.

---

### Post by djbushido on 2009-01-27
Okay, used dd for one, dcfldd for the other [partitions]. Turns out it is now using ~90 Gib, as opposed to copying about 6 of data. Huh?
Also, it's not booting correctly, I don't know how to make sure that grub is installed in boot record. Recognized by BIOS, but then hangs. not sure why, reset the UUID's, and updated grub.conf to reflect partition differences. And source drive was off.

---

### Post by djbushido on 2009-01-28
Okay, think I might have found the problem. According to some forums, the partition sizes have to be the same. That might be the problem. I'll try this, fix /etc/fstab, resize parts with gparted, reboot, and see what happnes. Wish me luck.

---

