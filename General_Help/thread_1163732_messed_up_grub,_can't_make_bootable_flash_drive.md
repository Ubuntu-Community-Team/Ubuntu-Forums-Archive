---
title: "messed up grub, can't make bootable flash drive"
date: 2009-05-19
forum: General Help
---

### Post by Giles on 2009-05-19
i messed up my grub trying to install gfx grub on my eee pc 1000. now i can't get into ubuntu or xp when i start up i just get a useless grub prompt.

my only other machine is running mac osx tiger. i have tried creating bootable flash drives with the command 

```
sudo dd if=easypeasy-1.0.iso of=/dev/disk2
```

but my eee doesn't seem to like them. i can easily take the hard drive out and mount it on my mac with a usb enclosure but my mac can't read ext3, and even if it could, would i be able to fix my grub that way, i don't think so. has anyone had any success with creating bootable usb drives from isos in osx?

cheers

---

### Post by Bindsa on 2009-05-19
Boot from the live cd and recover GRUB should work.

---

### Post by Giles on 2009-05-19
> **Bindsa said:**
> Boot from the live cd and recover GRUB should work.

i have no cd drive on my eee pc.

i did manage to make a bootable flash drive of ubuntu-9.04-alternate-i386.iso using netbootin, i will try to recover grub from there.

---

### Post by Giles on 2009-05-19
ok so i got all the way through system restore which took ages.

and then i got to the stage which says 

```
[!!] Enter rescue mode

You need to make the newly installed system bootable, by installing the GRUB boot loader on a bootable device. The usual way to do this is to install GRUB to the master boot record of your first hard drive. If you prefer, you can install GRUB elsewhere on the drive, or to another drive, or even to a floppy.

The device can be specified using GRUB's "(hdn,m)" notation, or as a device in /dev. Below are some examples:
- "(hd0)" or "/dev/hda" will install GRUB to the master boot record of your first hard drive (IDE);
- "(hd0,1)" or "/dev/hda2" will use the second partition of your first IDE drive;
-"(hd2,4)" or "/dev/hdc5" will use the first extended partition of your third drive (SCSI here);
-"(fd0)" or "/dev/fd0" will install GRUB to a floppy.

Device for boot loader installation

 (fd0)_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _  
<Go Back>                                              <Continue>
```

and i chose (hd0) and it just gives me a fatal error every time. should i be trying (hd0,0) or (hd0,1), i was too scared too in case i messed up my system even more.

---

### Post by Bindsa on 2009-05-19
What fatal error did it gave?

---

### Post by Giles on 2009-05-19
> **Bindsa said:**
> What fatal error did it gave?

i'd have to run through it again which takes like an hour (has to download extra packages). but i remember it was a very generic fatal error.

would using a livecd be easier? i might try download one at university tomorrow.

edit: forgot to mention i've been using the alternate 9.04 live cd image in recovery mode, booting from usb

---

