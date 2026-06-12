---
title: "Need GParted Help Urgently!"
date: 2009-03-27
forum: General Help
---

### Post by DizzyTech on 2009-03-27
Okay, my partition setup today was as follows:

250 GB hard drive - 232.88 "usable"
Partition 1:  192.88 GB NTFS, label "Windows"
Partition 2:  40.00 GB NTFS, label "Vista"

I had all my files on the first partition, until I moved all of them today to my second partition.  I started up the Hardy LiveCD I had, and then started GParted.

I deleted the first (192.88GB) partition, and hit apply.  I then told GParted to move the second partition to the front, and hit apply.

It didn't get far.  After moving the first 32 MB, the system *crashed*.

Here's where I am now.  Apparently, GParted made all the changes to the partition table already:

Partition 1:  40.00 GB NTFS (label name "Windows", according to Hardy LiveCD)
Partition 2:  192.88 GB unallocated (according to GParted)

Please, help!  How do I get my files (on the second partition) back?  Can anybody help me craft a DD command to get those 32 MB back where they belong?

---

### Post by DizzyTech on 2009-03-27
Please, please help.  I really need my files.

---

### Post by B4RR13N705 on 2009-03-27
But do you want to keep windows in your HD? if yes, try to resize the partitions.
If you want only to keep ubuntu, the i recomend you to format the whole HD and start a clean installation :)

---

### Post by drs305 on 2009-03-27
There is a app called *testdisk* that can be pretty helpful in situations like this. Some data on the first partition may have already been overwritten but in any case you should avoid doing anything to either partition that would cause the disk to be written to.

Take a look at this link or do a search of the forums:
[http://www.cgsecurity.org/wiki/TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")

---

### Post by dhughes on 2009-03-27
I don't know but I did find this: [http://ubuntuforums.org/archive/index.php/t-181625.html](http://ubuntuforums.org/archive/index.php/t-181625.html)

 It's more what to do first, not what to do with a failed move but it may help you.


edit:

 or this [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by DizzyTech on 2009-03-27
Well, I had two partitions.  I meant to get rid of the first (192.88 GB "Windows", NTFS) and move the second (40.00 GB "Vista", also NTFS) to the front.  GParted only moved the first 32MB, so I know it's all "still there."  I don't care if the physical area of the new first partition (40.00GB, NTFS, "Windows", empty) is blitzed, I just want my files from the 40.00 GB partition that was at the end of the drive and isn't anymore.

The Hardy LiveCD automounted the (new), glitched-out first partition on boot.  Attempting to play with it in GParted shows the orange yield/alert symbol, showing all sorts of errors and telling me to use scandisk in Windows.

I'm running the Hardy LiveCD right now, and TestDisk 6.10 is looking for partitions.  Can it really recover the old last partition, 32MB or not?  Should I run the deeper scan so it looks for superblocks, too?  It's already finding "old" partitions I had from not too long ago.

---

### Post by DizzyTech on 2009-03-27
I also used DD to copy the first 32MB of that glitched-out 40.00 GB partition (dev/sda2, BTW, there's no /dev/sda1) because it does appear to be the beginning of that 40.00 GB partition at the end of the drive... question is, how do I get it *back* there to wherever "238.88 GB - 40.00 GB" is?

Edit:  I also feel the need to repeat that the 192.88 GB at the end of my drive (after the glitched-out 40.00 GB one) is marked as unallocated.

---

### Post by DizzyTech on 2009-03-27
Does this sound good?
```
The following partitions can't be recovered:
     Partition               Start        End    Size in sectors
  HPFS - NTFS          17934 241 36 44043 201 30  419438560
  HPFS - NTFS          18812 233 46 44921 193 40  419438560

```

Of course, they could be old partitions... but I can't be sure.

---

### Post by DizzyTech on 2009-03-27
I'm sorry to keep doing this, but I really need help with this.  Could I use DD to copy that 32MB back to where it's supposed to be?  TestDisk is still running on Deep Scan, but you can see my previous post for the results of the regular scan.

Edit:  Good news.  Those two partitions that TestDisk detected don't seem to be my 40.00 GB partition from earlier since (using the equations (s*512)/1024/1024/1024 and (s*512)/1000/1000/1000 to get from sectors to GB) 419438560 sectors is nowhere near 40.00 GB.

---

### Post by DizzyTech on 2009-03-27
PLEASE!  I'm desperate.  I know that my files are there, and (as far as I know) the filesystem is still there... but how do I manually create the partition?

---

### Post by 2048Megabytes on 2009-03-27
[SIZE="3"]Do you have another computer that you could hook your hard drive up to?   This is my preferred way to pull files off a hard drive when the operating system isn't working.

May I also suggest in the future you buy an external hard drive to keep a copy of the data you value?  Hard drives don't last forever and a failed hard drive can cause you to lose many years of data.

Rosewill RX35-AT-SU SLV Aluminum 3.5" Silver USB 2.0 External Enclosure - $20
[http://www.newegg.com/Product/Product.aspx?Item=N82E16817182156](http://www.newegg.com/Product/Product.aspx?Item=N82E16817182156) 

SEAGATE Barracuda Model ST3250410AS 250 gigabyte SATA 7200 RPM Hard Drive - $55
[http://www.zipzoomfly.com/jsp/ProductDetail.jsp?ProductCode=10005934&prodlist=celebros](http://www.zipzoomfly.com/jsp/ProductDetail.jsp?ProductCode=10005934&prodlist=celebros)
[/SIZE]

---

### Post by DizzyTech on 2009-03-27
I need a custom user tag:  "1 Cup of Irony."  I have an external HD, but I use it for videos, backup documents, and emergencies.  In this case, the hard drive is fine... the partitions (not the filesystems) are obliterated, however.

---

### Post by 2048Megabytes on 2009-03-27
[SIZE="3"]I don't mean to sound rude at all, just trying to help.  But you didn't answer the previous question I asked. 

Do you have another computer that you could hook your hard drive up to?[/SIZE]

---

### Post by DizzyTech on 2009-03-27
I'm sorry, I was the one being rude.  No, I don't.  I'm in the midst of copying that area of the hard drive (232.88 GB - 40.00 GB, converted to bytes, divided by 512 as the "skip" parameter; 40.00 GB converted to bytes, divided by 512 as the "count" parementer; 512 as the "bs" paremeter) to my external hard drive to attempt to mount it as a filesystem using DD.  Tell me if that'll help at all.

In any case; here's the DD I'm using:
```
dd if=/dev/sda of=/media/Files/sys.img bs=512 skip=404498677 count=838860800
```

---

### Post by 2048Megabytes on 2009-03-27
[SIZE="3"]What is DD?  

My advice is to back everything up you value to a separate hard drive so you don't lose anything.  _Then_ you can mess with _another_ hard drive and attempt to repair your operating system.  Verify you can access the data you value on the separate drive before you start messing around with your current hard drive.

Also, when you begin to fiddle with trying to restore your operating system make sure you disconnect your back up drive from your computer.  

I remember hearing a story about someone who was playing around with their system with their external hard drive connected.  They wiped out all the data on their hard drive and the external drive as well simply because they didn't disconnect the external drive.
[/SIZE]

---

### Post by DizzyTech on 2009-03-27
dd is a Unix command-line utility for copying raw block datas between hard drives.  Once again, I must repeat that my issue is that I cannot mount that area.

---

### Post by 2048Megabytes on 2009-03-27
[SIZE="3"]Wish I could help you but I don't know a lot about Linux Operating Systems.  I love playing with some Linux Operating Systems occasionally but most of my experience is with the dreaded Microsoft Windows.  Hopefully someone else who has more knowledge than me in this area can help you out.[/SIZE]

---

