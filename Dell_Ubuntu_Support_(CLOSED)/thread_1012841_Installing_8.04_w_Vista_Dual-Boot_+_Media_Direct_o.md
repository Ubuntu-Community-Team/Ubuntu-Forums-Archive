---
title: "Installing 8.04 w/ Vista Dual-Boot + Media Direct on Inspiron 1520"
date: 2008-12-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Nutbar on 2008-12-16
So, I want to install 8.04 on my Inspiron 1520.

I was thinking of installing Ubuntu after my last final today. I am going to give up my desktop that has Ubuntu on it, and give it to my girlfriend, or store it. I don't use it much at all, and I need to desk space to study. I need a less bogged down OS to do my schoolwork and browse the net. I'm loathed to give up Vista at this point, as I am still clinging on to my gamer roots.
I want to Dual-boot with Vista, and keep Dell Media Direct (for the moment anyhow). Media Direct is version 3.3.

So far, I've shrunk my Vista partition so that there is 40gb unallocated space after the partition.

So, my drive setup looks as follows:
Extended Partition: ?? - 86mb
Primary Partition1: D:\ - Dell Restore Partition - 10gb
Primary Partition2: C:\ - Vista - 100gb
Unallocated space: 40gb
Primary Partition3: (Media Direct?) - 2.5gb

I've the Ubuntu 8.04 install/live cd. Am I able to install directly to the unallocated space without any issues? Providing that I boot directly to the Ubuntu cd and install from that point. I plan to use the Manual setup option.

I want to manually set up my partitions within the unallocated space. Formatting to ext 3, "/home" will have 20gb, Linux Swap will have 2gb, and "/" will have the rest of the space.

I'm not sure where to install grub to. I've read warnings of not installing it to the MBR. 

I'm trying to do this as safely as possible. Does anyone have any tips or pointers for me?

Thanks,

Terry

---

### Post by zwygart on 2008-12-16
I suggest you to boot LiveCD, add the home partition with gparted and then install by using the option use free space at step 4 (I think). Grub should not do any trouble. It will install the files in / and the stage1 in the MBR. No fear, your windows will be bootable. To play it very sure you could backup the mbr and the boot sectors of the partitions. Keep also a CD of windows near, (no matter if XP or Vista).

---

### Post by ytsejam1138 on 2008-12-16
Use Wubi to install your Dual Boot.  [http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by timcredible on 2008-12-16
you can only have 4 primary partitions, so you're going to have to make the unused space an extended partition because you need at least 2 partitions for linux (/ and swap).  i would make the following inside of that extended partition:

1gb - swap
6gb - /
the rest - /home

also, if i were you, i would use 8.10, not 8.04

---

### Post by Nutbar on 2008-12-17
Thanks for the help.

The Wubi install was not an option for me, as I don't want to run Ubuntu within the Vista OS. Plus, the way I set it up, I should be able to see all of my drives in either OS.

> 1gb - swap
6gb - /
the rest - /home

also, if i were you, i would use 8.10, not 8.04 

I followed this advice. After a few false starts, I finally installed Ubuntu 8.10 on the third attempt. I found that the major hitch was that the Canadian Repository has a crummy connection, and kept stalling me at 82% when it tried updating.

Everything is good so far. Thanks again!

- Terry

---

