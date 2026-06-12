---
title: "Deleting Vista partition through GParted on dual booted Ubuntu laptop."
date: 2009-05-25
forum: General Help
---

### Post by Mojo McCracken on 2009-05-25
Okay. I have a dual booted Vista/Ubuntu laptop.

But, because Ubuntu is so awesome (and thanks to the power of *Wine*), I would be delighted to relieve my hard drive of the pestering Vista, hogging ~80% of my HD.

So, how do I do this, without screwing up the whole thing?

I was thinking about deleting the Vista partitions (there's a disaster recovery partition also) through *GParted*, and then resizing the Ubuntu partition, to fit the whole HD. But is that even possible through *GParted*?

Also: Would such an action delete the GRUB (that's what I'm hoping)?

---

### Post by nikhilbhardwaj on 2009-05-25
Yes you can do this with gparted
which are your vista partitions
post the output of sudo fdisk -l

alternatively you could format those partitions and remove vista's entry from grub

---

### Post by networm1230 on 2009-05-25
hello friend

I just wipe my tow hard drives like to days ago it is vary easy to do I was duel booting vista and Ubuntu Linux but in tow different hard drives but now i am using Linux Ubuntu I no longer have vista installed on my PC. will hear are the steps. before you star you must know a few things. Windows uses fat32 and NTFS file system. Linux uses swap file system.

step.1 In Ubuntu Linux go to Applications than to Add/Remove.

step.2 now select (ALL) and ware is says show chose (ALL available applications)

step.3 now ware it says search. search for (Gnome Partition Editor) click in the box and hit Apply to install it

step.4 now to system than go to (Administration) now go down to (Partition Editor) and click on it

step.5 you must unmount you hard drive if it is mounted now click on (Gparted) that click on (refresh device) this will scan for your hard drives.

step.6 now click on (view) and click on both options. how to the small picture of a hard drive.  and chose your driver that you wont to format too (warning) pleas be careful select the right hard drive you wont to Partition of format look at Device information to mack share you chose the right Drive to format.

step.7 now right click on the big bar that say your mount point of you hard drive and space of your hard drive. Right click on the big bar and go to (format to) and choose your format and click apply. (Warning) this will erase all data from the drive.

NOTE:Remember the the operation system. Windows uses fat32 and NTFS file system. Linux uses swap file system.


Hope this helps you friend good luck!

---

### Post by merlinus on 2009-05-25
> 
Linux uses swap file system.
Perhaps you mean that linux uses ext3 or ext4 (or other) filesystem. and not fat, fat32, or ntfs.  swap is only used for the swap partition, which usually uses 1.5-2G and is set up whilst installing.

---

### Post by lisati on 2009-05-25
Two important things to keep in mind
[LIST=1]
[*]Make a backup of your recovery parition, even if you don't intend to put Windows back on your system,  "just in case" (e.g. if you need to put Windows back temporarily to keep the service people and warranty department happy) - many computers come with software to help with this task
[*]If you installed Ubuntu using "wubi" (i.e. you installed Ubuntu "within" Windows) then deleting all traces of Windows will also delete Ubuntu
[/LIST]

---

