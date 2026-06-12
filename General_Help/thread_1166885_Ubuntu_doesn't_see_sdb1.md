---
title: "Ubuntu doesn't see sdb1?"
date: 2009-05-22
forum: General Help
---

### Post by dvfreelancer on 2009-05-22
Okay, the last partition issue I had ended by blowing away the Linux partition and reinstalling Ubuntu 9.04 on a larger partition.  Resizing and moving just wasn't working.  

In the process, I discovered a new issue.  There's additional drive space on this laptop but I can't figure out how to get at it.

> Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: *******

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        3088    24756165    7  HPFS/NTFS
/dev/sda3            3089        4864    14265720    5  Extended
/dev/sda5            3089        4783    13615056   83  Linux
/dev/sda6            4784        4864      650601   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: ******

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38913   312568641    7  HPFS/NTFS


So, there it is, /dev/sdb1. But until I ran fdisk that's the first I knew of it.  Nothing in the install process...hey, there's another 320 gigs of drive space over here, you want some of that?  

Now what?  Back to the installation cd?  The partition editor in the live CD doesn't see it. Do I have to blow away the entire NTFS partition?  And with what?  

I think it's great I can work through some of these issues with help from you guys here, but new users coming from Windows world....they're never going to have the patience to work through something like this.  They wouldn't know where to start.

---

### Post by plucky on 2009-05-22
Are you dual booting with windows XP or Vista?

Read this link [url]http://www.psychocats.net/ubuntu/mountwindows[/code] for mounting ntfs partitions.

You can install gparted ```
sudo apt-get install gparted
```in Ubuntu and reformat the sdb1 partition once it is un-mounted.The only time you need to use the Live CD is when you have to work on the / system partition.

> I think it's great I can work through some of these issues with help from you guys here, but new users coming from Windows world....they're never going to have the patience to work through something like this. They wouldn't know where to start.

It does take time to learn a new operating system,as it did to learn Windows, but I think the effort is worth it.The best place to start is right here,reading as much as possible.


Good Luck

---

### Post by dvfreelancer on 2009-05-22
> **plucky said:**
> Are you dual booting with windows XP or Vista?

Read this link [url]http://www.psychocats.net/ubuntu/mountwindows[/code] for mounting ntfs partitions.

...snip...

It does take time to learn a new operating system,as it did to learn Windows, but I think the effort is worth it.The best place to start is right here,reading as much as possible.


Good Luck

Certainly I would agree.  And you can't expect any OS to be able to immediately adapt to any cobbled together pile of hardware, most of which were designed for a different OS.  

I'm just trying to keep the perspective of someone coming in new to all this.  

Now off to load gparted...

---

