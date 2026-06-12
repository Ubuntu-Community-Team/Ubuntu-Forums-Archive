---
title: "Mini 9 Swap File"
date: 2008-10-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bd_thompson on 2008-10-18
1. Would the Mini 9 be helped by a swap file?
2. If so, can an SD card be formatted and set up as a swap file?

---

### Post by az on 2008-10-18
> **bd_thompson said:**
> 1. Would the Mini 9 be helped by a swap file?
2. If so, can an SD card be formatted and set up as a swap file?

1.  Possibly.  Try it out and let us know.  I suppose it depends on what you do with it.  If you run a lot of apps at the same time, maybe it would.  If you just do simple stuff, you probably won't notice a difference.

2.  sudo mkswap /dev/sdXx (Xx is whatever partition you use.  Foe example, sdb1)

Then add it to /etc/fstab.  Find out it's UUID using the vol_id command.

Flash (NAND) memory has  a limited number of write cycles.  With proper load leveling, I reckon it would take many many years to reach the write limit on a common-sized Sd card (say 1 Gig)  A lot of people think the thing would wear out in a very short time - that just is not true.  I would not discourage the use of an SD card or a USB drive as swap space if it was useful.

---

### Post by Youresorock on 2008-12-14
I'm trying to do this right now..  When I put my SD card in the slot it automounts if it's FAT16.  There is no dev/sdX for it.  I put it in my card reader, and it was given dev/sdb.  I partitioned the whole thing (128mb) as a swap with gparted.  Then I put it back in the SD card reader, and it doesn't show up anywhere...

Humm....  In the SD slot, it doesn't show up in gparted.

I can tell the card is detected, because /dev/disk/by-id shows it.  But I don't know how I can mount it.

---

### Post by Youresorock on 2008-12-14
I found another forum page where it explained that the SD card reader in the Mini9 uses a different scheme in the  /dev than normal ATA stuff.

go to /dev and do 

ls mm*


to enable the swap I did

sudo swapon /dev/mmcblk0p1

That worked, so I added it to my fstab as usual for a swap partition.  

Only 128mb, but better than nothing until I order a big SD card.  I figured it was better to run swap on an easily expendable card than on the SSD.

PS:  I LOVE my mini9

---

### Post by armandh on 2008-12-14
prices are low 
picked up a 4Gb card as I am dual booting XP/8.10

---

