---
title: "Help with partitions and data"
date: 2006-08-31
forum: Desktop Environments
---

### Post by Wipster on 2006-08-31
Hey all
I have a few questions about partitions as I dont have a clue about them.
On my SATA drive at the moment I have my windows partition (NTFS) my linux root partition (ext3) my home partition (ext3) a swap partiton and a transfer partition (FAT) I would like to use the transfer to beable to move or store files but it cant 'mount' in linux, they are all primary BTW because I have no idea what primary and logical mean.

I also have another SATA drive which is NTFS which stores a few thigns atm which I would like to access from linux.

Ok now u know the mess in which my computers data is in, what would be the best way to organise it, swap file and a fat or fat32 partition on my second drive for storing data I wana access and windows, root and home on main, or swap on main aswell? hmmmmm got a feeling swap on another drive might be a lil faster because it can work at the same time, but I dont realy know.

And what is the deal with primary and logical and what do I need to have these partitions set to?

Sorry for all of that, I dont realy know where to start O_o :(

---

### Post by coffeecat on 2006-08-31
You are limited to 4 primary partitions on a drive. Or one of the four partitions can be an extended one - this is a 'container' for logical partitions. Windows has to reside on a primary partition - it cannot boot from a logical one, but other Windows partitions (D:, E:, etc) can be logical. Linux has no such restrictions. A Linux root partition can be primary or logical. With the Linux numbering convention for partitions you can tell which are logical. sda would be your first sata drive, and sda1, sda2, sda3 and sda4 are primary or extended on the first drive. Logical partitions are numbered sda5 or higher (or sdb5 for a secondary drive).

You have listed five partitions on one drive. They cannot all be primary - that is impossible. What does your disk manager tell you? (System > Administration > Discs  - in Gnome.) If you only have four partitions and they are all primary then you have a problem. You cannot create any more without deleting one first.

Mounting partitions:

Assuming your 'transfer' partition is sda2, in a terminal do:

sudo mkdir /media/sda2
sudo mount -t vfat /dev/sda2 /media/sda2

But then you need sudo privileges to read and write to it. Better would be to add a line to your fstab file so that it is mounted automatically at bootup for ordinary users to use. Post back if you want to do this with accurate details of your partition layout. You can also mount a ntfs partition with a line in fstab for read only. You can enable writing but this is still in development.

I have no idea whether putting swap on another drive would make it any faster - I should imagine it would make little or no difference at all.

---

