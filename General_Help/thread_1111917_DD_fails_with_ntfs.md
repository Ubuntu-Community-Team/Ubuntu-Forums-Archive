---
title: "DD fails with ntfs???"
date: 2009-03-31
forum: General Help
---

### Post by hsjC on 2009-03-31
I am trying to clone a windows partition to a new harddrive.

So first I copied over the MBR+Partition table info:

dd if=/dev/sdb of=/dev/sda bs=512 count=1

After that I checked sda and it does have the same partition info as sdb.

Then I went ahead with:

dd if=/dev/sdb1 of=/dev/sda1 bs=32M 

Strangely, after it's done I couldn't mount it as ntfs at all. It seems nothing was copied over or something.

Can someone point out where my flaw is? I'd really appreciate it.

---

### Post by aeiah on 2009-03-31
is there any reason for bs=32M? that seems rather large. i havent any experience with dd-ing ntfs though

---

### Post by HermanAB on 2009-03-31
Just copy the whole disk, then repartition to reclaim the unused space on the new larger drive:

dd bs=1M if=/dev/sdb of=/dev/sda

and let it rip till the end of the source disk.

---

### Post by hsjC on 2009-04-03
Man, I been busy the whole week.

I use bs=32M to optimize performance since the new drive is an SSD.

Unfortunately the old drive is larger than the new drive so I dont know what will happen if i do a full drive copy...

---

### Post by dcstar on 2009-04-03
> **hsjC said:**
> I am trying to clone a windows partition to a new harddrive.
..........

Then use the copy and paste function in the Partition Editor.

---

