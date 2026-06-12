---
title: "Wrong free space information after resize partition"
date: 2005-11-01
forum: Desktop Environments
---

### Post by neymac on 2005-11-01
I had two Ubuntus installed in my HD:
sda2=> Ubuntu 5.10 (5Gb, 2.8Gb free space)
Sda3=> Ubuntu 5.04 (5Gb, 2.1Gb free space)

Both working fine.

To increase space in Brezzy, I decided remove the Hoary and resize the Breezy.

With the Ubuntu 5.10 Live CD, I used GParted and did it.
All worked fine.

Then I started Breezy, and it loaded normally, but it says that the partition where it's installed (sda2) is 10Gb with the same free space (2.8Gb) it had before it's resize.

When I research Sistem=>Adm=>Disks I found in /sda2: 7.8Gb used space and 2.8Gb free space. 

Where have gone my 5Gb?

I've made research in several places, thought this forum an google and did not find solution for this problem. 
I've rebbot again with the Live Ubuntu 5.10, run GParted, and the free space shown is wrong as well (2.8Gb instead of 7.8Gb).

My Breezy is working so fine that I'm afraid to try anything without sure.

Is there any command line to fix the free space?

My HD partitions:
/sda1=> 20Gb NTFS (WinXP)
/sda2=> 10Gb ext3
/sda4=> 85Gb NTFS (WinXP Data)

I need this extra space to move the data from WinXP to increase Ubuntu's partition, and let the WindowsXP only as spare system.

---

### Post by Kyral on 2005-11-01
I think it may have altered the partition table data without deleting what was there. As for how to fix it, no clue this is the first time I have heard of this happening...

---

### Post by neymac on 2005-11-01
[QUOTE=Kyral]I think it may have altered the partition table data without deleting what was there. As for how to fix it, no clue this is the first time I have heard of this happening...[/QUOTE]

Yes, but I've removed the /sda3 (Hoary's partition) before resize /sda2 (Breezy's Partition) with GParted.

---

### Post by neymac on 2005-11-01
I tried shrink the partition /sda2 1Gb, using Live CD Ubuntu 5.10=> GParted.
It didn't shrink, but fix the problem: 
     Now /sda2 is 10Gb sized and 7.5Gb free space.

Problem fixed.

Thank's Kyral for the quick reply and the attention.

---

### Post by Kyral on 2005-11-01
No prob, though I don't really know what I did to help ;P

---

### Post by az on 2005-11-01
Perhaps you grew the partition, but not the filesystem?  You need to do both.  You can have a ten gig partition with a three gig filesystem on it.  In that case, you will see only three gigs of hard drive space when you mount the three-gig filesystem.  You need to tell the filesystem to extend itself to the end ot the partition.

Usually, though, Gparted and Qtparted do that for you....

---

### Post by neymac on 2005-11-02
[QUOTE=azz]Perhaps you grew the partition, but not the filesystem?  You need to do both.  You can have a ten gig partition with a three gig filesystem on it.  In that case, you will see only three gigs of hard drive space when you mount the three-gig filesystem.  You need to tell the filesystem to extend itself to the end ot the partition.

Usually, though, Gparted and Qtparted do that for you....[/QUOTE]

The Admin=>Disks tool showed the partition with 10Gb and 2.5Gb free space,
but the command line "df" (disk free, I think) showed 5Gb with 2.5Gb disk free in that partition.
Kyral told maybe the partition table was messed up. 
The only safe (or almost safe) way to rearrange the partition table that I know how to do is using the GParted. So I decided try to shrink the /sda2 partition 1Gb (change it 10=>9Gb)  and see if the picture would change.

When I tried do so, it didn't shrink and the GParted instead of shrink it, fixed it and show the 10Gb with 7.5Gb of free space.

I restart Brezzy and there was my lost 5Gb of free space back.

command line "df" and Nautilus show the same: 7.5Gb of free space.

I think the problem was solved.

Thank's

---

### Post by haydent on 2008-04-01
heres a little story of how i saved my  500gb hdd from being corrupted by windows ....

i keep it in external usb hdd bay, which has its own cheap issues but hasnt let me down yet...

basically i started out formateing the whole thing with ntfs when i forst got it and using it like that, but i ike linux and before long wished id formatted it ext. but by this tage it was too full for me to do anything about...

but then when it wouldnt mount in windows more and more and and i was getting ever more dispaired with windows scandisk i figured id better do something before it was any worse.

so spared up about 60gbs on other old drives and got the 500 down so only half was being used, after having plugged it into an ide cable and tower to read it as opposed to the usb case....

then i ran o & o defrag from in windows to defrag and move everything (~250gb) to teh first half of the drive, then i loaded up partition magic 8 to split and format the driev into 2 halfs. i tried boot-it ng and gparted but they both wouldnt touch it complaing to run chkdsk from windows as windows had marked it bad, but after running chkdsk /r several times, it still wouldnt unlock it. (partition magic did it anyway.)

then i copied everything over, formatted the first half to ext3, ran fsck.ext3 checking for bad blocks, (to find none) then copied everything back from the 2nd to the 1st partition. deleted the 2nd, and resized the 1st to take up all the hdd with gparted.


**this is where something went awol... **


all of a sudden i had one big ext3 partition that was saying it was full at ~480gbs when it should have been half full ? yet would only say it had ~250 gbs of data on it by certain apps)

after reading around the net i heard mention of resize2fs. and that perhaps what had happened was gparted had not resized the size of the filesystem...

so after running resize2fs /dev/hdb1 i had a full ok ext3 500gb drive again, with no bad sectors or data, that mounts in windows via ext2fsd.

:)

---

