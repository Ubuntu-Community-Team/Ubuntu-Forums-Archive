---
title: "3TB disk. 3GB of storage."
date: 2009-03-01
forum: General Help
---

### Post by britlion on 2009-03-01
Eventually I got parted to make my raid array into one ext3 partition of 3TB (almost) in size. The array is /dev/sda. The single drive for booting and system is /dev/sdb.

DF shows:

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb1            295976868   3126152 277815888   2% /
varrun                 2027444       528   2026916   1% /var/run
udev                   2027444      2776   2024668   1% /dev
tmpfs                  2027444       128   2027316   1% /dev/shm
/dev/sda1              2883620     69908   2784416   3% /media/mediastore

For some reason it thinks it is NOT 3TB. It appears under the name 3000MB disk on the desktop. parted thinks:

Model: Areca ARC-1210-VOL#00 (scsi)
Disk /dev/sda: 3000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name     Flags
 1      17.4kB  3000GB  3000GB  ext3         primary     

Which suggests it is formatted as 3TB.

Gparted agrees with parted - I assume it's a front end for it. It shows one primary partition of 3000GB.

If I go to a folder on the drive and right click for properties, it thinks there's just 2.8Gb of free space.

What is going on here???

---

### Post by Cybie257 on 2009-03-01
> **britlion said:**
> 
Number  Start   End     Size    File system  Name     Flags
 1      17.4kB  3000GB  3000GB  ext3         primary     

Which suggests it is formatted as 3TB.

Gparted agrees with parted - I assume it's a front end for it. It shows one primary partition of 3000GB.

If I go to a folder on the drive and right click for properties, it thinks there's just 2.8Gb of free space.

What is going on here???

That's normal. The bigger the drive (space) you have, the more you will notice it. There is overhead in the formatting process (can't think of the exact terminology, so bear with me.) that is using space on your drive.

I know it seems like a lot of space used, but it's more about percentage for the partition and directory tables. If you didn't have information written to disk to tell where things are, you wouldn't be able to save and read your disk. 

I just setup a 600GB Raid andonly have 538GB of available space. Take in account, that each one is telling a different story. Think about when you buy a brand new 1.5 TB drive, just as I recently did. It gave me a 1.38TB free space reading. It's sort of a deceiving thing that hard drive manufacturers use to sell 'bigger' drives than they are, but it is not false advertisement. This is what they do...

------------------------------------------------
BELOW IS INFORMATION FROM [http://www.dbstalk.com/showthread.php?p=1923528](http://www.dbstalk.com/showthread.php?p=1923528)
------------------------------------------------

The difference in space mentioned between a "1TB" drive and the 930.3GB of usable space reported by the OS can be entirely attributed to the marketing math I mentioned. To prove it, I'll show you the math.

Drive manufacturers state that 1KB = 1,000 Bytes and 1MB = 1,000KB = 1,000,000 Bytes, etc.

In reality 1KB = 1,024 bytes and 1MB = 1,024KB = 1,048,576 Bytes.

If you push this to the 1TB level where a drive manufacturer states that 1TB = 1,000GB there is a very large discrepancy which we can see by looking at that extrapolated out.

According to drive manufacturers...

1KB = 1,000 Bytes
1MB = 1,000,000 Bytes
1GB = 1,000,000,000 Bytes
1TB = 1,000,000,000,000 Bytes

In reality...

1KB = 1,024 Bytes.
1MB = 1,048,576 Bytes
1GB = 1,073,741,824 Bytes
1TB = 1,099,511,627,776 Bytes

Do you see the discrepancy between the listed capacity and how a TB would actually be calculated? It's 99,511,627,776 Bytes.

They didn't sell you a 1TB hard drive. They sold you a 1,000,000,000,000 Byte hard drive. 1,000,000,000,000 Bytes = 931.322575 Gigabytes

So you see, the marketing math problem does actually explain the discrepancy quite well.



Hope this explains it.. :) 

-Cybie

---

### Post by damis648 on 2009-03-01
> That's normal. <cut>

It is not, he said the partition is 3Tb while it says there is only 2.8Gb of free space (that's Gb, not Tb). What is the output of
```
fdisk -l
```
?

---

### Post by Cybie257 on 2009-03-01
> **damis648 said:**
> It is not, he said the partition is 3Tb while it says there is only 2.8Gb of free space (that's Gb, not Tb). What is the output of
```
fdisk -l
```
?

If that's the case, I apologize as I was 'assuming 2.8 TB'. (didnt notice 'GB')

Based on the output he provided, I would say that he meant 2.8TB and that would coincide with 2.8 vs 3.0.


Let's see what he/shehas to say in repsonse....

-Cybie

---

### Post by damis648 on 2009-03-01
> **Cybie257 said:**
> If that's the case, I apologize as I was 'assuming 2.8 TB'. (didnt notice 'GB')

Based on the output he provided, I would say that he meant 2.8TB and that would coincide with 2.8 vs 3.0.


Let's see what he/shehas to say in repsonse....

-Cybie

Look at the thread title. :popcorn:

---

### Post by Cybie257 on 2009-03-01
The Monday blues are already taking affect. :(

OK, so I missed yet another detail. Hmmmm. that's weird. 2.8GB. I'm definitely baffled now. But, if it were TB, then I would have been on to something. lol

-Cybie:confused:

---

### Post by britlion on 2009-03-01
Yes, I definitely meant that I am only getting 1/1000 of the storage space. I'm familiar with hard drive manufacturers using 1000 instead of 2^10 as a reference because it makes their drives look bigger.

Noting that fdisk does NOT support partitions greater than 2TB, here's fdisk -l:

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 2999.9 GB, 2999999791104 bytes
255 heads, 63 sectors/track, 364729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      267350  2147483647+  ee  GPT

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcf935e87

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       37435   300696606   83  Linux
/dev/sdb2           37436       38913    11872035    5  Extended
/dev/sdb5           37436       38913    11872003+  82  Linux swap / Solaris

---

### Post by Cybie257 on 2009-03-02
I'm trying to figure out the GPT partition format. What I am wondering is how easy it was for me to create a 5TB (6qty 1TB Drives) RAID 5, using Ubuntu 7.10 Desktop Version on a server I built for work.

I used mdadm for software RAID on a GigiByte Mobo (that has 8qty SATA ports). The total capacity via the GUI shows 4548.5GB formatted as an ext3 filesystem. It all showed up...

using fdisk -l, is complains about the drives not having a valid partition table, including the RAID (md0), but that probably is something to do with the fact the fdisk doesn't support partitions greater then 2TB.

I looked at the parted version of the RAID: here's what it said:

Disk /dev/md0: 5001GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number Start   End     Size      File system  Flags
 1     0.00kB  5001GB  5001GB    ext3


for each individual drive, it gives me a unrecognised label, which is expected. 


What level of RAID did you build (0,1,5)???

How many drives total? 

SATA/PATA??

Here is a website link that might have some useful information for you:

   [http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html](http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html)



Otherwise, I might suggest trying mdadm to create your array. Using this link ([http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)) makes it a very simple process to do. It only took me about 30 minutes (plus formatting time) to setup a RAID using this. Although I have lots of computer experience in many areas, this was the first ever RAID I ever setup. So, very easy and reliable. 12 months with no problems on the server I built. Also looks to be very simple to replace a failed drive. 

Not sure what I can help with the GPT partition table and what you are specifically dealing with, aside from the web link I provided, but maybe the mdadm might be a better way to go??? It works, all 5TB (4.5TB usable) shows up in GUI and other places. 

Hope I have been able to provide some sort of help. I'll try to keep up with your thread and see what else I can try to offer. 

-Cybie :)

---

### Post by fjgaude on 2009-03-02
I don't know of anyone with a 3TB partition... it could be a characteristic of many of the tools in Linux, as yet not upgraded to correctly recognize such large partitions.

You might consider writing a bug report and see what happens. Don't forget stating the GPT partition table.

---

### Post by britlion on 2009-03-02
> **Cybie257 said:**
> 

I used mdadm for software RAID on a GigiByte Mobo (that has 8qty SATA ports). The total capacity via the GUI shows 4548.5GB formatted as an ext3 filesystem. It all showed up...

using fdisk -l, is complains about the drives not having a valid partition table, including the RAID (md0), but that probably is something to do with the fact the fdisk doesn't support partitions greater then 2TB.



That's what I figured too - fdisk seems to understand the partition table to some extent, but it isn't happy about GPT at all. I partitioned the drive with parted, as per the usual recommendations about >2TB storage arrays.

Incidentally, the array is RAID 5, 4X1TB Hard drives. Sata, into a hardware RAID card into PCI Express.

I'll have a look at mdadm, and see what that is. Hadn't heard of it.

---

### Post by britlion on 2009-03-02
I looked into mdadm. So far as I can tell, this is for software arrays. I'm using hardware based: It already looks like one 3TB volume to the Linux system.

---

### Post by sloggerkhan on 2009-03-03
I was about to ask how your array was and sd* device on not an md* device, but you just answered that.

---

### Post by britlion on 2009-03-03
Aha. This particular bug takes a certain amount of idiocy.

1> Format with parted, and make the partition 3000MB, because you think parted works in GB, but it doesn't.

2> mkfs this 3000MB partition.

3> Realize you SHOULD have used a partition size of 3,000,000 not 3,000 and use parted to remake the partition.

4> (And this is the important one) forget to do mkfs again, so the filesystem on the partition is still the original 3GB one. Which miraculously survives a repartitioning, making it easy to forget you missed this step.

sudo mk2fs.ext3 /dev/sda1 

rebuilt all my inodes, and boo-yah. 3TB of space.

---

### Post by Cybie257 on 2009-03-03
Good deal. Glad to see you got it working. 

As for mdadm and software RAID. I was explaining to a guy at an off-site backup location (where I put the server I built) and he said that mdadm was a better choice compared to the hardware RAID built on to the motherboards. My curiosity is, did you build this RAID via the motherboard/BIOS RAID, or from an add-in card? 

The thing I like about mdadm is how easy it is to re-assemble the RAID. For example, I have 32-bit 8.10 Ubuntu, where I built the original RAID (at home) with 3 extra 300GB drives I had. I installed 64-bit Alpha 5 Jaunty, installed mdadm, one line command, and wholla... My RAID was right back online with my Jaunty install and is easily accessible via either distro I decide to load and run. 

BTW, Alpha 5 so far has proven to be (almost) release ready. Have only run into one problems, which was fixed via a patch 2 days later. :)

-Cybie

---

### Post by britlion on 2009-03-04
Hey again.

This is a hardware card, like I mentioned earlier. Specifically:

Model: Areca ARC-1210-VOL#00 (scsi)

So it has a dedicated specialist co-processor for dealing with the the raid array. It can even do raid 6 (though since this is only the four port version, I can't see why anyone would). In the original server, I have an 8 port hardware RAID 6 card. For both these cases, it's a PCI-Express card, and SATA drives.

Frankly, it spanks software RAID, and on board RAID.

I would expect on board to be better than software however. I can't imagine how it could be worse - in the worst case scenario, it offloads all the processing to the CPU. In any better case, it has dedicated hardware to doing the job. Software RAID has to process things like the parity information through the CPU, so in its best (and only) case, it's as bad as the worst case for on board.

The only possible exception is if the software version has a faster algorithm than the on board using the CPU. 

It's a general rule though that specific hardware > software.

Not that there's anything wrong with the software approach. For something that' got low CPU utilisation already, such as a dedicated file server, you're golden. Furthermore, should something really bad happen to the hardware you could put the drives in a whole new box and be able to read them as software RAID. If my hardware card goes poof, I have very few guarantees I can do that without buying a replacement identical card.

Sometimes speed isn't everything :)

---

### Post by sloggerkhan on 2009-03-04
> **britlion said:**
> Hey again.

This is a hardware card, like I mentioned earlier. Specifically:

Model: Areca ARC-1210-VOL#00 (scsi)

So it has a dedicated specialist co-processor for dealing with the the raid array. It can even do raid 6 (though since this is only the four port version, I can't see why anyone would). In the original server, I have an 8 port hardware RAID 6 card. For both these cases, it's a PCI-Express card, and SATA drives.

Frankly, it spanks software RAID, and on board RAID.

I would expect on board to be better than software however. I can't imagine how it could be worse - in the worst case scenario, it offloads all the processing to the CPU. In any better case, it has dedicated hardware to doing the job. Software RAID has to process things like the parity information through the CPU, so in its best (and only) case, it's as bad as the worst case for on board.

The only possible exception is if the software version has a faster algorithm than the on board using the CPU. 

It's a general rule though that specific hardware > software.

Not that there's anything wrong with the software approach. For something that' got low CPU utilisation already, such as a dedicated file server, you're golden. Furthermore, should something really bad happen to the hardware you could put the drives in a whole new box and be able to read them as software RAID. If my hardware card goes poof, I have very few guarantees I can do that without buying a replacement identical card.

Sometimes speed isn't everything :)

Most benchmarks I've seen show dedicated raid hardware and linux software RAID to be neck and neck performance wise. Probably you get more performance benefit from using scsi disks than you do from using hardware instead of software raid. That said, I can see how in some cases hardware raid can be easier to work with than software RAID.

---

