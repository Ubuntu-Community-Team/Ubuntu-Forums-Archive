---
title: "Hoary not even bootable after successfull install"
date: 2005-06-17
forum: Gaming &amp; Leisure
---

### Post by mrbit on 2005-06-17
could be hardware, it's all brand new, but after a successful hoary install i just can't boot from my hard disk

it's a DFI motherboard (groan, i think that was a mistake) model nF4-DAGF with 
processor AMD64 Athlon 3200+ also, 2GB of ram (do you care what brand?)

and a Maxtor 40GB hdd (which wasn't new...) - it's the master on the first ide bus, i've disabled the SATA bus(es) as i won't be using them for a little while

i booted back up using my other livecd and checked out hda1 (the hdd) and everything seems to be there, fdisk -l says hda1 is bootable... i'm stumped.  i did the install twice, same thing both times, the machine just halts citing no OS available...

yeah this guy knows:  ](*,) 

thanks y'all

---

### Post by jerrykenny on 2005-06-17
If the live cd works I wouldnt think it would be a motherboard problem,

Are you getting as far as the grub prompt ?

Have you checked your bios to see if you have write-protected the mbr ?

Check the boot sequence on your bios,  also that the IDE cables arent crossed (unlikely I know but your hard drive is maybe on the second IDE, or on a slave or something)

Whats your partition table like ?    I had an unsuccessful install with ubuntu once when I tried to use reiser file system . . . best to use ext3 for debian/ubuntu 



Stick with Grub bootloader rather than lilo, 


On an old hard drive which has had a previous linux install, check the partition table with cfdisk,  to ensure the partition table isnt corrupted.  Mandrake is bad for this.  I once had a hard drive which reported different conditions depending on whether i used fdisk or cfdisk.


Also if you can boot using the live cd, mount your partitions, do a chroot, then grub-install to the mbr, and see if you get any error messages.

---

### Post by mrbit on 2005-06-18
thanks jerrykenny, why did i post this in gaming though...
i moved the post over here and included responses to your replies

[http://www.ubuntuforums.org/showthread.php?p=218542#post218542](http://www.ubuntuforums.org/showthread.php?p=218542#post218542)

---

### Post by mtron on 2005-06-18
Just to make sure:

The boot order in the Bios is set to cdrom (or floppy) then harddisk? 

Also: did you try to disable the sata bus in the bios?

if yes, you must also set the right harddisk to boot from in the bios boot order. There must be a setting for choosing the boot order and a seperate one to choose the hd.

Check your Bios settings once more. it really sounds like a misconfigure.

---

### Post by MetalMusicAddict on 2005-06-18
Set your OS drive to LBA instead of AUTO in the bios. Its the "Access Mode"

---

