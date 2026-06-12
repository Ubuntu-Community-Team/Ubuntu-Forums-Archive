---
title: "Partitions when installing, I might have screwed up."
date: 2009-04-20
forum: General Help
---

### Post by Munnzy on 2009-04-20
Ok, I'm not really good at this and I followed some random youtube tutorial for dual-booting vista and ubuntu. I mostly winged it because the tutorial wasn't very good but this is what I did. (Sorry if there are a million of these threads, I didn't find any with my problem).

For my partitions, I created these two (after my main vista one):

4 GB (I think) set to use as ext3 and mount as /
and
70 GB set to use as swap.

I'm not sure, but are these supposed to be switched around?? My "home" folder said it only has 800 mb of space left, and I thought it was supposed to be the main storage place.

Again, sorry for the complete newbness.

---

### Post by drs305 on 2009-04-20
Yes, they are switched. You generally need no more than 2x the amount of RAM you have installed at the most. 

After an install on a 4GB partition 800MB might be expected to be all that is left, assuming you did a fresh install and haven't added any data files or additional apps.

If you haven't spent much time with this install you could reinstall it. Another option would be to resize the partitions using gparted from the LiveCD.  If the swap is on the right in gparted, you could delete the swap entirely and expand the / to the right, which would be faster than the other way around I think.

To run gparted, "*gksudo gparted*" in terminal or System, Administration, Partition Editor.

---

### Post by prem1er on 2009-04-20
First off how much space did you partition for your /home directory?  Also, if you are correct, you have allocated way to much swap space.  You should need about 1.5 * the amount of memory you have on your computer. Post the results of this in your terminal.

```
sudo fdisk -l
```

Thanks.

---

### Post by Munnzy on 2009-04-20
> **prem1er said:**
> First off how much space did you partition for your /home directory?  Also, if you are correct, you have allocated way to much swap space.  You should need about 1.5 * the amount of memory you have on your computer. Post the results of this in your terminal.

```
fdisk -l
```

it says cannot open /dev/sda


So I should just reinstall and set ext3 (I'm assuming this is the main location) for 70GB and my swap for about 8 since I have 4gb RAM?

---

### Post by drs305 on 2009-04-20
You have to run fdisk as root:
```

sudo fdisk -l

```

4GB of swap should be more than enough. You might try gparted to resize / and swap. It might be a bit faster than   a reinstall, especially if you just delete swap and expand / to the right if that is where the free space is. I expanded my first post if you didn't see it all.

---

### Post by Munnzy on 2009-04-20
> **drs305 said:**
> You have to run fdisk as root:
```

sudo fdisk -l

```

woops, here it is

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3cca3cca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       50993   409601241    7  HPFS/NTFS
/dev/sda2           50994       60801    78782760    5  Extended
/dev/sda5           50994       51601     4883728+  83  Linux
/dev/sda6           51602       60801    73898968+  82  Linux swap / Solaris

---

### Post by drs305 on 2009-04-20
I'd recommend using gparted from the LiveCD. Delete sda6 (swap), then expand sda5 to the right, then recreate swap again. I personally always stick swap at the far right in gparted since I wouldn't ever change it's size.

If this doesn't make sense and you need further clarification just ask.

By the way, welcome to the ubuntu forums!  :-)

---

### Post by Munnzy on 2009-04-20
> **drs305 said:**
> I'd recommend using gparted from the LiveCD. Delete sda6 (swap), then expand sda5 to the right, then recreate swap again. I personally always stick swap at the far right in gparted since I wouldn't ever change it's size.

If this doesn't make sense and you need further clarification just ask.

I have gparted, but If I run it and mess with the partitions, wouldn't it mess up linux files on those partitions? I'm thinking it would be easier for me to go and remove the partitions and reinstall it and set the partitions again with the installer. Would deleting the partitions on vistas disk manager basically uninstall ubuntu, then I can just reinstall? Even if it's completely unnecessary to do this, Im not really sure how to do other things.

---

### Post by drs305 on 2009-04-20
gparted, ubuntu's partition manager, can resize partitions without destroying the data. Of course, with any repartitioning there is always the risk of data loss.

I believe Window's partitioning tool will recognize the two linux partitions if you are more comfortable using it. I sent you a private message offering assistance with some details if you want to try gparted. It would be a quick learning experience, but that's up to you.

---

