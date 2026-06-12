---
title: "Partiton scheme advice"
date: 2009-04-23
forum: General Help
---

### Post by endtime on 2009-04-23
Hey all, I did try searching for posts about this but didn't see anything.  So I'm building a new PC, and my plan is to dual boot Ubuntu and Windows 7.  My drive will be a 640 GB SATA drive (well, actually two of them in RAID 1).

I'm trying to decide how to partition my drive.  I'll be using Ubuntu for schoolwork and development, and Windows for gaming.  AFAIK Ubuntu has pretty good NTFS read/write, so I could go with something like 50 GB for Ubuntu and 590 for Windows.  Are there any pros/cons for doing that vs. doing something like 50 GB for each OS and then a 540 shared data partition?  I guess this is, in part, a Windows question too.  Are there any benefits to having things like music stored and games installed on the Windows OS partition?  Because if I want to reinstall Windows when new builds come out it would be nice to have that stuff separate.

---

### Post by aloshbennett on 2009-04-23
The biggest advantage I can think of of keeping data separate from OS partition is that, if you want to go for a re-install your data would be safe.

Infact, I keep my root and home drives separate under ubuntu.

---

### Post by Menschenfresser on 2009-04-23
In all cases put /home in a different partition/disk. Mine has survived the switch from different distros (mandriva > suse > ubuntu) and a ubuntu reinstall (had downloaded the 32bit version instead of the 64bit one) without much fuss. Since you have the data somewhere else it doesn't need to be very big.

---

### Post by endtime on 2009-04-23
Cool, thanks.  Presumably, /home needs to be an ext3 partition right?  I'm actually thinking of doing something similar with Windows...so does that mean I want four partitions?


[ Windows - NTFS ][ Shared data, game installs, documents, etc - NTFS][ /home - ext3 ][  / - ext3  ]

Does that look right?  What are reasonable partition sizes, given that my drive is 640 GB?  I'd like to have the shared NTFS partition as large as possible without making any of the others too small.

---

### Post by Menschenfresser on 2009-04-23
Yes, /home must be ext3, ext4 or any other filesystem that supports linux permissions. As for the size, I'd give / around 10GB. For /home it depends if you plan e.g. to manage your pictures in f-spot, the collection gets pretty big with time. If not, then you'd be on the save side with >6GB.

Also, it's a good idea to reserve a partition for swap. It's not really needed if you have enough RAM, but you won't be able to hibernate if you don't have one at least as big as your RAM.

---

### Post by endtime on 2009-04-23
Yeah, I typically let the installer do its thing (other than telling it how much space it has), and it creates a swap partition by default.

I don't really do the photo library thing, and even if I were going to I'd want that on the shared NTFS partition.  /home will just be for my Ubuntu-specific stuff.

---

