---
title: "Installed on SATA drive and upon reboot no grub."
date: 2006-08-10
forum: Desktop Environments
---

### Post by Flaystus on 2006-08-10
I just installed Ubuntu into a PC I've had it on before. The only difference is its now has a SATA drive.

Ubuntu saw and installed on it just fine, but upon reboot I gives an error loading operating system instead of GRUB.

Help? ;)

---

### Post by patrickfromspain on 2006-08-10
ok, boot into the live cd, open a terminal and:

sudo grub
there:

root (sd0,x), where x is your ubuntu partition-1 (if ubuntu is on sda6 you'll have to put sda5 and so on)
setup (hd0)
quit

and restart

hope it helps!

---

### Post by Flaystus on 2006-08-10
Sadly. YOu just lost me.

How do I know which one it needs to be on?

SDA1?

---

### Post by Flaystus on 2006-08-10
Ok tried 

root (sd0,sda1)


This is just an assumption. I have no idea how to tell and create the hda sda numbers as I can't see a list of partitions anywhere (suggestion?)

Either way I get this error.
"Error 23: Error while parsing number"


update: It appears to be SDA3 that Ubuntu is on.

---

### Post by Ocxic on 2006-08-10
ok in linux you do not have a C: D: E: A: drives, there is the root / wich is kinda like the topmost containg folder, everything under / is all of your directories, and files on it. everything on linux is a file or a folder, there is no distiction between a .txt and .exe extensions, this allows for much simpler and IMHO a much more user friendly filesytem.

linux, or at least in ubuntu gives hard drives and cdroms, and floppy drives special files in /dev (that is a folder on your / (root) filesystem, that contains speacial "device files" that are use to define and run all your computers hardware).

Hard drives first 2 letter are always "hd" (or "sd" for SATA hard disks)
the letter following hd(x) is the acctual identifier
EX (replace "hd" for "sd" when using an SATA drive):
hda is the Primary Master IDE drive.
hdb is the Prinary Slave  IDE drive.
hdc is the Secondary Master IDE drive. 
hdd is the Secondary Slave IDE drive.

lastly we have the number at the end
hda(#)
this is the partion number that point to the partion you wish to use
type "sudo fdisk -l" in a terminal/console to find out how many, and the whats-what of your computers partitions, and hard drives.
While also telling you what the filesystem type is, and giving you the name of the drive you would use.
```

ex:
admin@BennettNet-C1:~$ sudo fdisk -l
Password:

Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          12       96358+  83  Linux
/dev/hda2              13       14946   119957355   8e  Linux LVM

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       24321   195358401   8e  Linux LVM


```

thats what i get to give you an idea of what to look for.

now that you understand that we can move to grub, your bootloader.

Grub is what makes your computer go (after the BIOS) and turns on ubuntu for you.

follow patrickfromspain's instructions to re-install grub.

Grub uses a diffrent naming sequence but is just as easy and similer to what i just explaind to you

"(hd0)" would be "hda" or "sda" 
"(hd1)" would be "hdb" or "sdb"
and so-on

"(hd0,0)" would be "hda1" or "sda1"
etc...

the only thing i find with Grub is that if you have both an "hda" and "sda"
"(hd0)" can mean both to grub, and i find that IDE drives over-rule SATA drives (at least for me) so you may have to change your hardware config if that is a conflict for you i can also help with that.
(IDE drives use a wide, thin grey cable, SATA drives have a thin narrow ussually red cable (these are inside your comp))

that sould be all the knoledge that is required to know to get you goin, and get your system running.

---

### Post by Flaystus on 2006-08-10
Thanks for the rundown. Fdisk was the command I needed to see the partitions. Thanks.

Here is the current situation.

Based on another post here I installed with the standard IDE drive (2nd drive) unplugged. Works great, but the moment I plug it back in GRUB gives an error.

But at least GRUB IS running now. I tried to change the root currently reads root (HD0.1) and of course 0,0 for Windows boot.

What do I need to do to change this because editing it to sd0,x (tried 1 through 3 though my linux partition itself is 3) and it had no effect.

Also Windows tells me NTLDR is missing which its never done with Ubuntu previously.

---

### Post by Flaystus on 2006-08-10
Also I'd hate to change my hardware setup because the standard IDE drive is an old 2mb Cache drive and the SATA is a 8mb Cache drive.

---

