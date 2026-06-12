---
title: "Resizing Windows Partition"
date: 2006-07-24
forum: Desktop Environments
---

### Post by Lucidio on 2006-07-24
Hello everyone!

I want to resize my Windows partition to give more space to Ubunto. My HD has only 20 GB: Windows 14.5 GB and Ubuntu 4.5 Gb.

But i only have about 1 GB free in Ubuntu, How can i resize the patitions table in a safe way?

Another thing: Where i can find a step by step guide to switch completely to Ubuntu (Elminating the window partition) without loosin all the data of Ubuntu.

:confused:

---

### Post by mmcmonster on 2006-07-24
tools you should look into include gparted and qtparted on linux and partition magic on windows.

The best way to do this is to run gparted or qtparted from a livecd, since non of the partitions will be mounted at that time, and then delete the windows partition (if that is your plan).  Once the windows partition is deleted, create a new Linux partition.

Caveats -
1.  I don't know of any application that can resize an ext3 partition.
2. Back up /home and any other data directory before you begin this process.
3. If you cannot get your partitions just like how you want it, delete all of them and start from scratch.  Since you backed up /home, you should be (relatively) safe.

3a. If you do delete everything and start from scratch, make sure /home is a separate partition so that you can delete / and reinstall linux without losing your data in the future.

---

### Post by aysiu on 2006-07-24
Wait--what do you want to do? Do you want to resize Ubuntu to give it more space... or do you want to get rid of Windows completely?

---

### Post by Lucidio on 2006-07-24
Initially i want to resize my windows partition so ubuntu can win more space, maybe in a near future eliminate windows but conserving my ubuntu in its actual status

---

### Post by herrdoktor330 on 2006-07-24
> **mmcmonster said:**
> tools you should look into include gparted and qtparted on linux and partition magic on windows.

The best way to do this is to run gparted or qtparted from a livecd, since non of the partitions will be mounted at that time, and then delete the windows partition (if that is your plan).  Once the windows partition is deleted, create a new Linux partition.

Caveats -
1.  I don't know of any application that can resize an ext3 partition.
2. Back up /home and any other data directory before you begin this process.
3. If you cannot get your partitions just like how you want it, delete all of them and start from scratch.  Since you backed up /home, you should be (relatively) safe.

3a. If you do delete everything and start from scratch, make sure /home is a separate partition so that you can delete / and reinstall linux without losing your data in the future.


Hello,

I'm having a similar problem with Ubuntu. I'm trying to remove my windows partition completely and it's being a major pain.

I've tried using the steps above, using the live disk to use the Gnome partition editor. I got an error stating that the device was too busy to complete the action (deleting the partition). When I boot back to my current installation, it still reads the partition as NTFS. I've tried formatting from there, with no results.

What should I do? I don't want to reinstall ubuntu from scratch, as I've done a couple kernel compiles and got everything working the way I wanted it to.

---

