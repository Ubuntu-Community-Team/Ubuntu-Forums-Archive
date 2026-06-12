---
title: "Partiton Manager?"
date: 2005-10-29
forum: Desktop Environments
---

### Post by ArcadePride on 2005-10-29
Im hearing a lot of different things, so I was wondering what is the generally accepted best partition manager for kubuntu? Partition Magic in my windows partition wont let me touch my linux partition and i have to resize them. All opinions welcome, so whats your favorite partition manger for the kde ubuntu?

thanks-a-bundle

---

### Post by adwait on 2005-10-29
qtparted, gparted.

---

### Post by clearnitesky on 2005-10-29
Yup, that's what I was going to say. qtparted is more for kde and gparted for gnome, but it really doesn't matter

---

### Post by Cuppa-Chino on 2005-11-19
okay I here **gparted** and **qtparted** everywhere, but the real question is does anyone of these perform better - and I do not mean the GUI - do they both use the same programm libraries for the operations or does one have a better set?

I presume it is safest to resize partitions with a *live cd* - any ideas? 

which filesystem should one use for Linux, I hear lots of mentions for **ext3** but also a lot of support for **Reiser FS** - any advantages with either?

is it possible to _safely_ defragment my FAT32 shared partitions from Linux?

thanks

---

### Post by asimon on 2005-11-19
[QUOTE=Cuppa-Chino]okay I here **gparted** and **qtparted** everywhere, but the real question is does anyone of these perform better - and I do not mean the GUI - do they both use the same programm libraries for the operations or does one have a better set?
[/quote]
Yes, they both use the same library libparted. qparted and qtparted are just different GUIs for the same thing. The actuall logic and partition modification happens in libparted. Thus just use the GUI you prefer.

[QUOTE=Cuppa-Chino]
I presume it is safest to resize partitions with a *live cd*[/quote]
Yes.

[QUOTE=Cuppa-Chino]
 - any ideas? 

which filesystem should one use for Linux, I hear lots of mentions for **ext3** but also a lot of support for **Reiser FS** - any advantages with either?
[/quote]
Both are excellent. I think there are some very long threads about which filesystem is best. Each one has it's fans. Generally reiserfs has better performance with smaller files, and ext3 has better latency.

[QUOTE=Cuppa-Chino]
is it possible to _safely_ defragment my FAT32 shared partitions from Linux?
[/QUOTE]
I dunno.

---

### Post by PokerFacePenguin on 2005-11-20
[QUOTE=ArcadePride]Im hearing a lot of different things, so I was wondering what is the generally accepted best partition manager for kubuntu? Partition Magic in my windows partition wont let me touch my linux partition and i have to resize them. All opinions welcome, so whats your favorite partition manger for the kde ubuntu?

thanks-a-bundle[/QUOTE]


Personally, I have just resized some Kubuntu partitions (ext3) using parted on the knoppix cd.
Since alot of programs seem to have problems altering ext3, it is not too bad to convert them to ext2 temporarily (ext3 is ext2 + journaling).  Then you can convert them back after resizing.

It is important to fsck them before you do this process.  Never modify a mounted partition. A knoppix cd will work fine.

fsck -f /dev/yourpartition to resize
tune2fs -O ^has_journaling /dev/yourpartition to resize (this removes journalilng)
parted          (used to partition/modify partitions)
******* ? at parted prompt will give you syntax
tune2fs -j /dev/yourpartition to resize (turns journaling back on the partition)

modify the /etc/fstab entries and grub if you need to

reboot

---

### Post by Cuppa-Chino on 2005-11-20
[QUOTE=PokerFacePenguin]
fsck -f /dev/yourpartition to resize
tune2fs -O ^has_journaling /dev/yourpartition to resize (this removes journalilng)
parted          (used to partition/modify partitions)
******* ? at parted prompt will give you syntax
tune2fs -j /dev/yourpartition to resize (turns journaling back on the partition)

modify the /etc/fstab entries and grub if you need to

reboot[/QUOTE]
Thanks for the help but unfortunately no chance for me. On my SATA HD, I have a couple of windofs partions. 
Primary NTFS with windofs
Logical  with a) NTFS, b) FAT32, c) free space & d) Linux SWAP
Primary with Linux ext3

**what do I want to do?**
[LIST]
[*]move swap to start of free space in logical partition
[*]shrink the logical partition so that there is space behind
[*]grow my ext3 filesystem into the free space
[/LIST]

booted with Knoppix 4.0.2 managed to fsck my data partition, not my swap unfortunately and then entered parted. In parted could not select my SATA HD so did not work.
Also tried qtparted, managed to select the swap and chose move command, but all it did was rescan all my drives....

Any ideas (Partition Tragic also does not work)???

---

### Post by Cuppa-Chino on 2005-11-20
managed to move the swap file & change the logical partition by booting into Knoppix with "noswap" (type knoppix noswap at boot prompt) 
still got no clue how do grow my other partition, it is my root for Ubuntu but that should not make any difference..

---

### Post by roland on 2005-11-20
[QUOTE=Cuppa-Chino]is it possible to _safely_ defragment my FAT32 shared partitions from Linux?[/QUOTE]

I have managed to resize a FAT32 partition once without any problems, although I did that with **cfdisk**. That is a console program, like fdisk in DOS, with a similar user interface but more options. See a screenshot [here](http://www.eff.org/broadcastflag/cookbook/cfdisk.png).

---

### Post by Cuppa-Chino on 2005-11-20
got it all to work

thanks PokerFacePenguin instructions were right! have rewritten them to make clearer for any slow newbie like me!

[LIST]
[*]move swap to start of free space in logical partition and shrink the logical partition so that there is space behind
[List][*]boot knoppix with "**knoppix noswap**" and then start qtparted with "**sudo qtparted**" [/list]

[*]grow my ext3 filesystem into the free space
boot knoppix with "**failsafe**" command (just failsafe will do) then follow PokerFace: 
[LIST]
[*]fsck -f /dev/yourpartition_to_resize
[*]tune2fs -O ^has_journaling /dev/yourpartition_to_resize *(this removes journalilng)*
[*]parted *(used to partition/modify partitions)*
[*]in parted select the right device e.g. /dev/hda *no letter for the partition just the device*
[*]move/resize commands as needed *(I needed to move "forward" on disk before I could resize*
[*]
tune2fs -j /dev/yourpartition_to_resize *(turns journaling back on the partition)*
[*]modify the /etc/fstab entries and grub if you need to
[*]reboot
[/LIST]
[/list]
might not be the smoothest way, possible do in one boot with failsafe, but it worked for me (and that is the main thing)

---

### Post by ajgreeny on 2005-11-23
This may or may not help, but I wanted to reduce the size of my WinXP partition to make room for a second installation of Ubuntu (Breezy this time as I already have a great working system with Hoary).

I read somewhere that the partition tool in the installation disks of Mandriva is the best available so I gave it a whirl.  After a defrag of the winxp system, I started up as if installing mandriva and went right through the partition manager where you can resize all partitions it finds. I then formated the new one I made as ext3.  I saved the new partition table and exited the Mandriva installation with a reboot, restarted and installed ubuntu on the new ext3 partition.

I don't know what other people think of this as a way to get where you want but it certainly worked for me with no hitches at all.  Give it a try and see how you get on.  Good luck!

---

