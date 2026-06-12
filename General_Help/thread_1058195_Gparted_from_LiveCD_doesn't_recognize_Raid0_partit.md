---
title: "Gparted from LiveCD doesn't recognize Raid0 partition"
date: 2009-02-02
forum: General Help
---

### Post by UranUtan on 2009-02-02
Hi,

I would like to resize an existing partition to make room to install Ubuntu 8.10.

Current machine: Vista Business x64, 4 GB RAM, Raid0 with two 500 GB SATA disks. The motherboard chipset is nVidia nForce 630i / GForce 7100. Vista x64 works OK so I assume my hardware is stable.

Vista x64 sees the entire stripe disks as a single unit of 1000 GB that I have split into some principal and extended NTFS partitions.

I would like to free 300 GB on an extended partition. For this, I boot the computer using the Ubuntu 8.10 Desktop x32 Live CD. I then open GParted which could recognize the striped disk of 1000 GB. In stead, GParted sees two disks each with 500 GB with an unknown parition.

I actually have a pooman's solution, just moving files within Vista and I will probably free an entire partition and destroy this partition to make room for Ubuntu.

However I would like to understand the technical part of the solution:

Q1. How can I use GParted on a Raid0 disk?

Q2. If I have a free extended partition, is it possible to install Ubuntu 8.10 x64 Desktop on this partition using the alternate CD? Can the installer recognize the Raid0 disk? 

Q3. Let assume that Q2 is solved. Can I use the 500 GB NTFS parition to split it into several other partition for Ubuntu? 20 GB for / 10 GB for swap and the remaining for /home (I have 4 GB RAM). The content can be destroy so there is no pb to reformat to ext3 FS. BTW is ext3 the recommended FS?

Q4. I plan to use GAG as multiboot manager ([http://gag.sourceforge.net/](http://gag.sourceforge.net/)) if you have any advice in this area, I would appreciate to learn.

Thanks in advance for any help.

---

### Post by UranUtan on 2009-02-02
Can anyone please help for a few hints, just for enough directions on where I should document further? Thanks.

---

