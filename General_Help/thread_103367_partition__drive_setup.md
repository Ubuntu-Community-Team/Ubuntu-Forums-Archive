---
title: "partition / drive setup?"
date: 2005-12-14
forum: General Help
---

### Post by not_yet on 2005-12-14
I tried to convince a friend of mine to move to Linux, but I guess he's not ready yet:( 

Anyways I'd like to return his hard drive to the way I found it.

Currently at start up grub starts and you can select windose or ubuntu.

partitions are c and d

there is a linux swap plus a partition for ubuntu.

I'd like to recover the linux partitions and convert them to ntfs and add the space back to the storage partition.

whats the best way to do this?

should I just nuke the linux partition? / will windows still start? ( no grub?)

I don't have acess to partition magic

thanks

---

### Post by soulestream on 2005-12-14
you should be able to delete the linux partitions with either a linux live cd using fdisk(cfdisk) or parition magic. The you can recreate the ntfs partitions with XP. 

as far as joining them, you probably can, but i like leaving working partitions alone. 

as far as booting, pop in the XP disk and go to recovery console and fixmbr (may be fix -mbr). I havent done it in so long i cant remember

soule

---

### Post by aysiu on 2005-12-14
A live CD is the best way to do this. Do you have Knoppix handy?

---

### Post by not_yet on 2005-12-14
thanks for the comments

I don't have knoppix / have the ubuntu live cd

what about using an old windose boot disk and fdisk?

---

### Post by stuporglue on 2005-12-14
I second the proposal to leave working partitions alone. Use the windows disk to fix the mbr, then from within Windows you can open the partitioner and format the other partitions. 

Your friend will have C: (the main partitioin), as well as D: and E: (or something -- the formerly Linux partitions.). If the two Linux partitions are side by side, you could join them with gparted, but I'd still not touch the Windows one.

---

### Post by psusi on 2005-12-14
You will need to run FIXMBR from the windows recovery console to remove grub and have windows boot normally.  You can boot up the ubuntu livecd and fire up gparted, blow away the linux partitions, and extend the ntfs partition into the free space.

---

### Post by not_yet on 2005-12-14
thanks all:) 

time for zzzzzzzz's

will work on it tomorrow

cheers

---

