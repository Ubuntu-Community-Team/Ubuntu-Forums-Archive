---
title: "Cedega question"
date: 2006-10-22
forum: Gaming &amp; Leisure
---

### Post by idarco on 2006-10-22
Right, my linux partition is pretty small. I've only 800mb free on it. My main hd partition has nearly 50gb free. However, when I tried to install a game in Cedega, I could only install it on my linux partition, which of course doesn't have enough space. Is there a way to get Cedega to install a game on the other partition? I don't want to resize my linux partition and risk messing it up in the process.

Thanks

---

### Post by handy on 2006-10-24
I have recently used GParted from the Dapper LiveCD, to delete, create resize multiple partitions on 2 different drives, 1 x SATA & 1 x PATA.

I resized my **/** partition, deleted the Swap partition, & created another data partition, all on the same PATA drive.

Then I resized the partition on a SATA drive, so I could make the new Swap & Var partitions on the same drive.

I trust GNOME Partition Editor (GParted). Using it would be a simple way that you could solve your problem.

Also, you may find [this how-to]("http://www.psychocats.net/ubuntu/separatehome") very interesting?

---

### Post by 1oki on 2006-10-24
> **idarco said:**
> Right, my linux partition is pretty small. I've only 800mb free on it. My main hd partition has nearly 50gb free. However, when I tried to install a game in Cedega, I could only install it on my linux partition, which of course doesn't have enough space. Is there a way to get Cedega to install a game on the other partition? I don't want to resize my linux partition and risk messing it up in the process.

Thanks

Cedega is just a pretty GUI with some added capabilities for WINE and By default the wine directory is /home/username/.wine

You might be able to change this in the WINE config file... but I never tried it. I have a seperate /home partition :)

---

### Post by handy on 2006-10-25
> **1oki said:**
> Cedega is just a pretty GUI with some added capabilities for WINE and By default the wine directory is /home/username/.wine

You might be able to change this in the WINE config file... but I never tried it. I have a seperate /home partition :)

Some of those capabilities are pretty powerful, like legal copy protection handling.

---

### Post by ookami on 2006-10-25
You should be able to do it by:
1. creating a folder on the partition you want to install to
2. moving the contents of ~/.cedega to your new cedega directory on the disired partition (make sure you get the .* files as well)
3. delete ~/.cedega
4. ln -s /your/new/fancy/dir ~/.cedega

that should do it

---

