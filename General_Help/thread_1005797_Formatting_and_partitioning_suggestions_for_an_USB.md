---
title: "Formatting and partitioning suggestions for an USB HD 500Gb"
date: 2008-12-08
forum: General Help
---

### Post by ilSignorCarlo on 2008-12-08
Hi,
I've just bought an external USB hard disk of 500gb.

- I'm going to use it to store files that I need almost every day, just because I'm on a laptop and I have to so much free space on it.

- I want to put on it also the whole mp3 library (quite big) and all videos and pictures I have.

- I need to use it with Linux and Windows.

1) How do you suggest to format it? I know that NTFS is ok for both Linux and Windows. Are there other choices?

2) Shall I make some partition on it? Maybe useful to make a partition for mp3, another for videos, another for other files and so on? Any suggestion about? What kind of partition do you usually create?

3) Is it possible to create a partition to run a virtualized Windows Xp?

4) Or another one to test some Linux distro?

5) Any other strange or useful suggestion? I have a lot of free space :P

6) This is the most important question, I think, but I remembered about it just now: how can I format the hard disk from the command line?

Sorry to ask so much questions and thanks for your help.

---

### Post by malathion on 2008-12-08
Yes NTFS will work with both linux and windows. FAT32 is usually the accepted filesystem for USB disks because of its universal portability, but you will run into some limitations with this (4GB file size limit, and it's not journaled). 

For my Usbuntu disk, I have the majority of the disk partitioned in ext3 and I use the ext2 installable filesystem to read it when I need to access it from Windows. More info here: [http://www.howtoforge.com/access-linux-partitions-from-windows](http://www.howtoforge.com/access-linux-partitions-from-windows)

It is very easy to get ubuntu running on a USB hard drive. In fact, I am typing this message from one I have running on a public computer lab right now! I have not heard of this being done with Windows XP, but I presume that it would work, if you could get the right drivers installed.

You can format the disk from the command line with the mkfs command, but I would recommend using gparted for this purpose.

---

### Post by ilSignorCarlo on 2008-12-08
> **malathion said:**
> Yes NTFS will work with both linux and windows. FAT32 is usually the accepted filesystem for USB disks because of its universal portability, but you will run into some limitations with this (4GB file size limit, and it's not journaled).

Yes, I excluded this option.

> For my Usbuntu disk, I have the majority of the disk partitioned in ext3 and I use the ext2 installable filesystem to read it when I need to access it from Windows. More info here: [http://www.howtoforge.com/access-linux-partitions-from-windows](http://www.howtoforge.com/access-linux-partitions-from-windows)

I see. But do you think there are advantages in using ext3/ext2 instead of NTFS?

---

### Post by malathion on 2008-12-11
> **ilSignorCarlo said:**
> I see. But do you think there are advantages in using ext3/ext2 instead of NTFS?

For starters, you do not need to defragment ext3. Also NTFS support is very reliable in linux now, but nevertheless it is still only reverse-engineered AFAIK so for me, I would not choose to trust it with a linux installation.

---

