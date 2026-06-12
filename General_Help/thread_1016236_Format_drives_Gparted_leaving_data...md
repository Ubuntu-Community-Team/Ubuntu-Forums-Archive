---
title: "Format drives? Gparted leaving data.."
date: 2008-12-19
forum: General Help
---

### Post by DamonChyld on 2008-12-19
How does one go about completely formatting a drive? 

I have been using gparted from the system rescue cd but when I delete partition, create a partition table, and create new partition it shows data as still being used. The drive is a 160g, after format is shows as a 149.01g drive with 2.52g used and 146.49g available. 

I am sorry if I am asking a obvious question, my searches inevitably come back pointing to gparted as the best solution so I must be overlooking something...

Thanks in advance!

---

### Post by civillian on 2008-12-19
There is no cause to find another tool to format your disk. This is probably your disk, since they are almost never the size they say they are (my 500GB disk is actually 465.7GB) so it's nothing to do with gparted, rather its the way that the drive is constructed and the way it is sold.

---

### Post by taurus on 2008-12-19
What filesystem do you use?  Remember ext3 will reserve 5% of the disk space for root in case you fill it up, you can still log in to do some deleting.  Of course, you can set it to 0% if you wish.

---

### Post by Jordanwb on 2008-12-19
```

dd if=/dev/zero of=/dev/sda

```

Your drive will be zeroed. However the dd command is very slow. I can copy a large file onto a partition at 25MB/s but dd goes at 10MB/s :-k

---

### Post by wpshooter on 2008-12-19
Get [www.killdisk.com](www.killdisk.com) and WIPE your drive and you will know that there is NOTHING on it at all.  This assumes there is absolutely nothing on it that you NEED !!!

---

### Post by DamonChyld on 2008-12-19
Thanks for the replies all.

It does bug me how they advertise a drive with X amount of storage, but when you get it home you inevitably see that it is X - ~10%, but that is why I assumed the drive size shows up as 149g vs 160g? 

I use the ext3 filesystem, but wouldn't the 5% be around 7.5g versus the 2.5g that shows as being used? That's nice to know about the built in failsafe, and that there is a way to disable it if needed though! A quick google search turned up [this little gem]("http://wiki.archlinux.org/index.php/Ext3_Filesystem_Tips") for anyone interested.

I tried the kill disk method, but the 2.52g still shows as being used, which seems rather odd. I will try the dd method over the weekend, am I correct in assuming that this is the right syntax 
```
dd if=/dev/zero of=/dev/sdb
```
for a fdisk -l of
```
Disk /dev/sdb: 160.0 GB, 160000000000 bytes

```
I don't want to inadvertently 0 out the wrong drive! :lolflag:

Also, this is actually one of 2 drives that are experiencing the same problem. The other is a USB 120g drive that shows as a 111.79g with 1.94g used. Both of these drives were NTFS and I used Gparted to delete partition, create a partition table, and create new partition, assuming that the data would get erased with the reformat. Could the issue have something to do with this?

---

### Post by logos34 on 2008-12-19
> **DamonChyld said:**
> but that is why I assumed the drive size shows up as 149g vs 160g? 

... 

Also, this is actually one of 2 drives that are experiencing the same problem. The other is a USB 120g drive that shows as a 111.79g with 1.94g used. 

Like C!V!NT says,
> 
they are almost never the size they say they are (my 500GB disk is actually 465.7GB) so it's nothing to do with gparted, rather its the way that the drive is constructed and the way it is sold.

in other words, it's an advertising ploy to make the drives look bigger.  Manufacturers conveniently define 1 GB = 1,000,000,000 bytes (base 10 exponential), whereas every OS sees 1 GB = 1,073,741,824 bytes (base 2 binary, or 2^30). So a 160 GB is really = ~149 gb,  and a 120 gb = ~114 gb

---

