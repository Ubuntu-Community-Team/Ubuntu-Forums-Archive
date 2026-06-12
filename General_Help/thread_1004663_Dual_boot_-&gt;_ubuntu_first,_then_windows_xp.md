---
title: "Dual boot -&gt; ubuntu first, then windows xp"
date: 2008-12-07
forum: General Help
---

### Post by Onay on 2008-12-07
I have an XP SP3 OEM disk, and my hard drive is partitioned so that the main partition is for ubuntu (ext3) and the swap partition. I am very happy with my setup, but I need to install windows so that I can manage my ipod touch 2nd gen (no support in ubuntu).

Last time I tried the dual boot, I partitioned to make an empty ntfs partition using gParted boot disk, but then I installed windows on that disk. But then when I used my windows disk, it said that the partitioned needed to be formatted, so I quick formatted and it wiped the entire disk.

I very much want to keep my setup right now... How can I safely set up my dual boot and/or backup my entire disk so that if something goes wrong I can restore what I have?

---

### Post by MarblePanther on 2008-12-07
XP *will* allow you to format a partition and not the whole drive.
You must have not been paying close enough attention during windows setup :p

Download supergrubdisk and burn to cd so you can restore grub when windows overwrites it.

Buy a usb harddrive and back up your files from ubuntu.

That's really it

edit: first resize your ubuntu partition with gparted and create any type of partition you want for windows.  Then install windows.

Pay close attention during windows install ;)

---

### Post by Onay on 2008-12-07
I have super grub disk and I backed up the menu.lst... so should everything be good otherwise? And should I use gparted or the ubuntu liveCD to partition (i have a separate gparted boot disk).

---

### Post by MarblePanther on 2008-12-07
The partitioner on the live cd is gparted
You should be fine if you have your files backed-up and supergrubdisk burned properly

---

### Post by Onay on 2008-12-07
I have super grub disk and I backed up the menu.lst... so should everything be good otherwise? And should I use gparted or the ubuntu liveCD to partition (i have a separate gparted boot disk).

---

### Post by theozzlives on 2008-12-07
You will have to activate Windows, possibly call Microsoft and tell them what you're doing (and why).

---

### Post by MarblePanther on 2008-12-07
Why the repost?

Gparted is the same on the livecd and your gparted cd--it doesn't matter

---

### Post by MarblePanther on 2008-12-07
theozzlives, what do you mean?  Yes, windows will make its partition active--thats what supergrubdisk is for.

Or are you talking about authenticating the product?  That's kinda standard with windows, why would he/she contact microsoft? I'm not sure what you mean

---

### Post by Elfy on 2008-12-07
If all I'm doing is partition work I always a partition editor - if you have the gparted livecd use that, I prefer partedmagic.

While there is a version on the buntu livecd - it takes longer to boot :)

---

### Post by TeXtonyx on 2008-12-07
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)


Continue to page 2: Back up the GRUB boot menu
    Page 1 Intro
    Page 2 Back up the GRUB boot menu
    Page 3 Make space for XP
    Page 4 Install Windows XP
    Page 5 Restore the GRUB boot loader

TeX: Be careful with Page 4, look it over.
You have already made a partition for XP. Leave it unallocated.
Then during the install use that un-partitioned space. You can't 
overwrite Ubuntu if you *don't install*, to a Partitioned space,
select an Unpartitioned Space.

---

### Post by Onay on 2008-12-07
> **TeXtonyx said:**
> [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)


Continue to page 2: Back up the GRUB boot menu
    Page 1 Intro
    Page 2 Back up the GRUB boot menu
    Page 3 Make space for XP
    Page 4 Install Windows XP
    Page 5 Restore the GRUB boot loader

TeX: Be careful with Page 4, look it over.
You have already made a partition for XP. Leave it unallocated.
Then during the install use that un-partitioned space. You can't 
overwrite Ubuntu if you *don't install*, to a Partitioned space,
select an Unpartitioned Space.

Thank you so much, I'm sure that was my issue before. Well here goes nothing thanks again

---

