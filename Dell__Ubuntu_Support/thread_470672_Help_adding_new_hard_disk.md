---
title: "Help adding new hard disk"
date: 2007-06-11
forum: Dell  Ubuntu Support
---

### Post by binary_dream on 2007-06-11
Dear folks,

I have decided to buy a new HDD (SATA) for Kubuntu, on my primary HDD i have XP sp2 installed, that old hdd is 80 GB SATA, but the new one is 160GB. I want to remove win XP on the new HDD, and on the old one install kubuntu.
I can't afford fresh new install of windows, I have a tons of data and software, do you guys now a way to transfer windows with its all content to the new HDD?

I have DELL PC(Optiplex Gx 620 N series, 1GB RAM, 3Ghz, ATI Radeon graphic card ... ), I have never installed before a hard disk, can you give me an advice on how to do it physically?


In desperate need for help,

Thanks a lot
Binary

---

### Post by rscott5 on 2007-06-11
> **binary_dream said:**
> Dear folks,

I have decided to buy a new HDD (SATA) for Kubuntu, on my primary HDD i have XP sp2 installed, that old hdd is 80 GB SATA, but the new one is 160GB. I want to remove win XP on the new HDD, and on the old one install kubuntu.
I can't afford fresh new install of windows, I have a tons of data and software, do you guys now a way to transfer windows with its all content to the new HDD?

I have DELL PC(Optiplex Gx 620 N series, 1GB RAM, 3Ghz, ATI Radeon graphic card ... ), I have never installed before a hard disk, can you give me an advice on how to do it physically?


In desperate need for help,

Thanks a lot
Binary

You should check out the Trinity Rescue Kit. It is a bootable Linux CD that includes ntfsclone which will copy an ntfs partition. You may have problems going from an 80GB to a 160GB drive, but I'm not really sure. Assuming you don't have any problems with the different drive sizes, ntfsclone will copy the entire partition byte for byte, meaning it will be able to get EVERYTHING. You will also need to copy the boot sector from the original drive. Read up on ntfsclone, that might just do the trick for you.

---

### Post by crjackson on 2007-06-13
> **binary_dream said:**
> Dear folks,

I have decided to buy a new HDD (SATA) for Kubuntu, on my primary HDD i have XP sp2 installed, that old hdd is 80 GB SATA, but the new one is 160GB. I want to remove win XP on the new HDD, and on the old one install kubuntu.
I can't afford fresh new install of windows, I have a tons of data and software, do you guys now a way to transfer windows with its all content to the new HDD?

I have DELL PC(Optiplex Gx 620 N series, 1GB RAM, 3Ghz, ATI Radeon graphic card ... ), I have never installed before a hard disk, can you give me an advice on how to do it physically?


In desperate need for help,

Thanks a lot
Binary

I do this sort of thing ALL the time.  I use Acronis TrueImage 9.1WS and Acronis TrueImage 8.

You could probably download the trial version and do just fine.  Just read the limitations on the trial version to make sure 1st.

Acronis TI has been and IS the most powerful and fastes tool I've ever used for this type of operation.  It's worth 10x the purchase price, I've used it for years.

---

