---
title: "Help with Raid / Large disk size"
date: 2009-02-12
forum: General Help
---

### Post by Crashinit6 on 2009-02-12
Hi All,

Please bear with me as this is the first time writing on this forum and still getting to grips with the formatting and what's needed.

I have just recently purchased 4 Seagate barracuda 1.5 Terrabyte drives which is now running in RAID 5. The total capacity is 4.09TB. I am having trouble getting the drives to partition as one with the total capacity. It seems that the maximum I can get is 2TB.

As far as what I have researched, Ext3 should be able to handle 4TB fine?
I was successful in creating 2TB partition with fdisk but not with gparted.
Fdisk also gave me this warning:

The number of cylinders for this disk is set to 547089.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Disk /dev/sdb: 4499.9 GB, 4499967049728 bytes
255 heads, 63 sectors/track, 547089 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c29e7


Any help will be much appreciated.

---

### Post by bodhi.zazen on 2009-02-12
I moved this post form Tips & tutorials to General help where I hope it will be more visible.

---

### Post by Slim Odds on 2009-02-12
Well, this wikipedia article says that an ext3 volume can be up to 16TB [http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)

Also, your output shows a /dev/sdb of 4499.9 GB, so where is your /dev/md? raid?

---

### Post by Crashinit6 on 2009-02-13
Hi Slim Odds.

Thanx for the quick reply.

I had a look in the dev folder and could not find anything refering to /dev/md? or RAID. What I did was that I deleted the 2TB partition that fdisk created which just leaves the drives unallocated. 

What am I missing here?

---

### Post by Slim Odds on 2009-02-13
I don't know about drives that large, but I've set up a RAID0 on my machine with two 320G SATA drives.

I used the alternate install CD which has mdadm support in it.

You partition your spaces as Linux RAID and then assemble them into the array. Once they are assembled, then you can format the array /dev/md0 (for example) as ext3.

For anyone who hasn't tried it, RAID0 is **AWESOME**. The doubled disk speed to excellent.

---

### Post by Crashinit6 on 2009-02-13
OK so this is what I did.

A bit of history. Windows and Linux has the 2TB drive partition limit when the partition table is set to msdos. Even though your drive is bigger than 2TB you will only be able to create a 2TB partition and loose the rest of the space.
This [resource]("http://www.carltonbale.com/2007/05/how-to-break-the-2tb-2-terabyte-file-system-limit/") helped.

What I did was still have one raid volume of 4TB, but I changed the partition table to gpt which has better support for larger partitions. There are pros and cons to this but this will work for me.

I used the command line tool called parted and did this:


```
(parted) mklabel                                                          
New disk label type? [msdos]?gpt                                          
(parted) print

Disk /dev/sdb: 4500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
(parted) mkpart
Partition name?  []? DISK4T
File system type?  [ext2]? ext3
Start? 0                                                                  
End? 4499900                                                          
(parted) print                                                            

Disk /dev/sdb: 4500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name    Flags
 1      17.4kB  4500GB  4500GB               DISK4T       

(parted) quit                                                             

```

unfortunately parted does not support the ext3 file system so once I done all the above I started gparted and created it there.
Once that was done I just added a rule in my fstab file to automatically mount it. All seems to be working fine.

I will test it some more to see if I hit into any problems and let you know.

Thanks for your help.

---

