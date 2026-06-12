---
title: "Inspiron 640m Partitions"
date: 2008-02-06
forum: Dell  Ubuntu Support
---

### Post by chezzo on 2008-02-06
Hi, I've got a Dell Inspiron 640m running Windows XP, and am hoping to install Ubuntu to dual-boot. My first step is to create two new partitions, one primary partition for Ubuntu and one extended partition for the Linux swap space and a FAT32 partition for sharing between Windows and Linux. I'm using GParted on the "Linux System Rescue CD".

My problem is that my hard drive already has 3 partitions, so I am unable to create the 2 more that I need. The drive is divided as follows (in this order): 78MB FAT (EISA Configuration), 69.89GB NTFS (my C: drive), 3.15GB FAT32, and then some unallocated space at the end.

So obviously for this to work I'm going to have to remove one or more of these partitions. I think the 3.15GB section belongs to Dell MediaDirect. Since I never use this I don't care about removing this partition, but is it safe for me to do so? And any ideas about that 78MB section? Alternatively, are there any tools I could use to discover what's on it and whether it's safe to remove?

Any help would be hugely appreciated, I am determined to get this to work!

---

### Post by chezzo on 2008-02-07
Well, I went for it anyway :)
Did a bit more research and found that the MediaDirect data is stored in the HPA, and it seems that the 3.15GB section was most probably a backup image (I vaguely remember Norton Ghost being installed on the laptop when I first got it). I decided I didn't need that and deleted it, then made my new partitions without a hitch.
I left the 78MB partition at the beginning of the disk since I'm not sure what it is.
Haven't installed Linux yet, but hopefully that should go just as smoothly.

---

### Post by chezzo on 2008-02-16
It did :p

---

