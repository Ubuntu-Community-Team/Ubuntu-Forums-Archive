---
title: "Defragment Ubuntu"
date: 2009-05-16
forum: General Help
---

### Post by compnut41 on 2009-05-16
What Ubuntu program would fragment my hard disk like on windows? Or is it even possible, (I know it will destroy OSX).

---

### Post by gettinoriginal on 2009-05-16
No you don't really need to defragment it, but if you really want look here
[http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)

---

### Post by chewit on 2009-05-16
You can defrag Ubuntu, providing you are using ext4

---

### Post by b@sh_n3rd on 2009-05-16
> **chewit said:**
> You can defrag Ubuntu, providing you are using ext4

You missed the best FS....XFS! :D

---

### Post by Ux64 on 2009-06-06
It seems that defrag program isn't ready yet?

Does anyone know schedule when it should be actually ready?

[http://lwn.net/Articles/284529/](http://lwn.net/Articles/284529/)

---

### Post by markharding557 on 2009-06-06
defrag on linux is not needed

---

### Post by oldsoundguy on 2009-06-06
Linux file management does not FRAGMENT files like Windows does.  Therefore, defragmenting is NOT needed.

---

### Post by ceciliaFX on 2009-06-06
I used Red Hat for years before I updated to Ubuntu and I never had a problem with fragmention


it's another reason to like linux

---

### Post by jrusso2 on 2009-06-06
All filesystems fragment.  Some less then others.  Depending on how you use your computer will determine if you will need to defragment or not.

Pydefragment is made for ext 3.

---

### Post by colau on 2009-06-06
> **oldsoundguy said:**
> Linux file management does not FRAGMENT files like Windows does.  Therefore, defragmenting is NOT needed.
That sounds good.
:D

---

### Post by -kg- on 2009-06-06
> **jrusso2 said:**
> All filesystems fragment.  Some less then others.  Depending on how you use your computer will determine if you will need to defragment or not.

Pydefragment is made for ext 3.

I totally agree, and especially if the partition is nearly full.  I have heard that it is possible to defragment a partition by copying the data on it elsewhere then reload it, preferably after the partition is expanded.

I Googled Pydefragment and could find nothing on it.  Is that the correct spelling?

---

### Post by rocket777 on 2009-06-07
So, ext3 filesystems don't get fragmented???? Here's my story...

I installed a brand new 9.04 system only _a week_ ago. I use it to run vmware vm systems, so like video files, it produces a few large files. Somehow, one of the files got extremely fragmented, as the following report shows.


$ filefrag *
OS1.vmdk: 125 extents found, perfection would be 1 extent
OS.vmdk: 883 extents found, perfection would be 68 extents
OS.vmem: [COLOR="Red"]105229 [/COLOR]extents found, perfection would be 5 extents


here's ls on these 3 files,

-rw------- 1 et et  75M 2009-06-06 21:22 OS1.vmdk
-rw------- 1 et et 8.2G 2009-06-06 21:22 OS.vmdk
-rw------- 1 et et **512M **2009-06-06 21:22 **OS.vmem**

This takes a very long time to even cp to the null device (after a reboot when the file is not cached). iotop says it's going at 3 mb/sec, while the larger file, which is not fragged goes at about 40 mb/sec.

$time cp OS.vmem /dev/null

real	1m39.892s
user	0m0.016s
sys	0m0.384s


I *defragged* it by copying it to another partition. Here's a frag report of the copy.

$ filefrag /media/sda6/win2000-2/OS.vmem
/media/sda6/win2000-2/OS.vmem: 6 extents found, perfection would be 5 extents

$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             56649688  29792760  23979288  56% /
/dev/sda6             58113948  15544084  39569728  29% /media/sda6

The parititon with the badly fragged file is only 56% used too. I've never had it more than 60% in use during this one week. The files were copied to this system from another system over my lan and so they should have begun as fairly contiguous files. 


So.... how in the world did this file become so fragmented??? [-o<

UPDATE:

I just did a little test and renamed the file, made a copy and then ran vmware 3 times. All I did was start it and then stop it. The fragments grew from

$ sudo filefrag *
OS1.vmdk: 125 extents found, perfection would be 1 extent
OS.vmdk: 883 extents found, perfection would be 68 extents
OS.vmem: 815 extents found, perfection would be 3 extents
OS.vmem-bad: 105229 extents found, perfection would be 5 extents



$ sudo filefrag *
OS1.vmdk: 125 extents found, perfection would be 1 extent
OS.vmdk: 883 extents found, perfection would be 68 extents
OS.vmem: [COLOR="Red"]14854 [/COLOR]extents found, perfection would be 3 extents
OS.vmem-bad: 105229 extents found, perfection would be 5 extents

---

### Post by -kg- on 2009-06-07
> So, ext3 filesystems don't get fragmented???? Here's my story...

I installed a brand new 9.04 system only a week ago. I use it to run vmware vm systems, so like video files, it produces a few large files. Somehow, one of the files got extremely fragmented, as the following report shows.

Apparently, you aren't the only one:

[http://communities.vmware.com/thread/16009]("http://communities.vmware.com/thread/16009")

From my reading, I would say it's more a vmware issue than a filesystem issue.  Nonetheless, I do agree with you (and jrusso2) that ext2/3 (and 4, else why would they have a defragger for it?) can become fragmented.  It isn't as easy as with FAT or NTFS, but it still can happen.

You might want to do a little research on the vmware/file fragmentation issue.  The above is just one example of what I came across.

---

### Post by Ux64 on 2009-06-08
Hey guys!

I did ask for STATUS!

Not that BS about, if it's needed or not. 

Defrag isn't needed with windows or fat systems either. Fragmentation doesn't lead to data corruption, so it's NOT needed on any modern file system. Including any old FAT. Performance can degrade if it's not done, but so what? System still keeps working. We had tons of servers with FAT filesystem, and we didn't ever defrag those. And it wasn't a problem.

---

### Post by TrakerJon on 2009-06-08
Defrag (or fidefrag I should say)

sudo apt-get install bzr python-psyco
bzr branch lp:fidefrag
cd fidefrag/src
sudo python fidefrag.py -d /<directory name>

Needless to say all file systems get fragmented...yes, even UNIX and Linux...and it does improve performance to "defrag".

I format using ReiserFS (much faster accessing smaller files) but I've used fidefrag on ext3 and ext4 formatted drives as well. You want to avoid defragging the /sys directory, I usually just defrag /usr /home /var /lib and /etc

---

### Post by rocket777 on 2009-06-08
> **-kg- said:**
> Apparently, you aren't the only one:

[http://communities.vmware.com/thread/16009]("http://communities.vmware.com/thread/16009")

From my reading, I would say it's more a vmware issue than a filesystem issue.  

Yes, it does appear that my problem is caused by some pathological case in vmware. I was able to do an strace on it but could not see what might be causing the huge increase in fragmentation on the one file.

That file is vmware's memory snapshot, or where it saves memory when you close the program so that on restore it appears to come out of hibernation. I wonder if it is a problem of vmware trying to shink and expand this file - all I could tell from the strace was that it does do a number of ftruncate64 calls, but I couldn't catch it when it was increasing the fragmentation.

I was able to cause it to occur by changing the size of the virtual machine's memory allocation, which caused this file to grow. But if I make a copy, and replace it with the copy, the copy is not fragmented and then it remained unfragmented through at least a few starts and stops. 

But something in ext3 is very prone to severe fragmentation. I guess if all you do is create and delete small files, then ext3 doesn't have a fragmentation problem.

Since I have an easy workaround, I don't have the time to keep chasing this problem, however. At least I know what's going on, when it was taking minutes to startup, instead of seconds, I thought my disk was starting to go bad - at least I now know that's not the case :)

---

### Post by Supersquirrel on 2009-06-13
Those files are highly fragmented because they are slow growing files. Most filesystems have that problem.

---

### Post by Sef on 2009-06-13
Ubuntu automatically defrags ext3 every 25 boots or so.

---

### Post by jacksaff on 2009-06-13
> **Sef said:**
> Ubuntu automatically defrags ext3 every 25 boots or so.

No, it runs fsck (file system check) which checks the disk to see if it is in an internally consistent state - ie. the tables that point to the actual files really are pointing to the actual files. This can be messed up by bad shutdowns such as pulling the plug so that the computer stops before all disk writes are completed.

---

### Post by night_fox on 2009-06-13
ext3 sure as hell gets fragmented if your partition is nearly full. It gets fragmented anyway, but it's designed to place the fragments so as to minimise fragmentation. I've never been able to tell how much of a performance hit you get from fragmentation, but it must be something, and I'd be quite happy to leave my laptop on overnight every so often to defrag it. I use ext3 for filesystems with large files, but my new gentoo root partition is reiserfs because I want speed. ReiserFs defrags itself in the background.

BE VERY CAREFUL IF YOU USE EXT4. A disadvantage is that its so backwards compatible with ext2/3 that older gparted (like the one on the hardy LiveCD) think it's ext3 and resize it accordingly, destroying some of the data. I corrupted my root ubuntu partition that way including /etc/hostname, and fixing it was what I spent my entire day today doing (its now 2:39 AM).

---

### Post by Arup on 2009-06-13
Unlike NTFS, Linux FS like ext3 or reiser or xfs don't fragment to the extent NTFS or FAT32 does. I have run both systems on parallel and my findings are that Windows fragments far more frequently when large files are moved. Compared to that the fragmentation issue if any on Linux FS is minimal and doesn't impact system. If fragmentation was an issue in Linux, there would be commercial level enterprise defragmenters like Perfect Disk and Diskeeper on offer. Obviously thats not case.

A good write up which explains fragmentation in Linux can be found here at [http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

---

### Post by night_fox on 2009-06-13
Yes but has anyone actually copied the same files to NTFS and ext3 partitions of equal sizes and then quantitively checked the fragmentation? From 0% to 100% full?

---

### Post by rocket777 on 2009-06-14
I am running vmware player on both windows 2000 and ubuntu 9.04 and each runs the same VM (config and files), and the same version of vmplayer. On windows, I've never seen ANY fragmentation problem at all using NTFS running vmware, while on ubuntu I can get severe fragmentation simply closing down the program (using the same data files on both systems). 

And the file that gets fragmented severely is one of only 10 or so files in this entire partition I built just for it and the partition is only 5% used. So, something strange is happening here.

But blaming this on vmware player is like the system admin who would say:

"Gee, the system would run just fine if it weren't for those pesky users running all those programs!"

---

### Post by Ux64 on 2009-06-15
> **Arup said:**
> 
findings are that Windows fragments far more frequently when large files are moved.


Can't be true. Move doesn't affect allocation in anyway.

> 
A good write up which explains fragmentation in Linux can be found here at [http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

It's over simplified and extremely bad example. I'm sorry about that. It's ultimate BS that has been fed to people that doesn't really understand what it's all about.

---

### Post by Ux64 on 2009-06-15
> **night_fox said:**
> Yes but has anyone actually copied the same files to NTFS and ext3 partitions of equal sizes and then quantitively checked the fragmentation? From 0% to 100% full?

Yet another problem with your sample. If makes all the difference if file is preallocated or not. If I use windows file manager to copy files, it seems that they do not get fragmented at least heavily. But if I use application that doesn't make pre-allocation then files do get fragmented some times quite badly.

Because ext3 doesn't even support pre-allocation, it means that there is no way to make perfect file placement. So files is going to be fragmented.

It would be good idea to read specs before making tests, so you would know what you're testing and what kind of results you should expect.

---

### Post by Arup on 2009-06-15
> **Ux64 said:**
> Can't be true. Move doesn't affect allocation in anyway.



It's over simplified and extremely bad example. I'm sorry about that. It's ultimate BS that has been fed to people that doesn't really understand what it's all about.

Believe it or not, I see your blatant defense of antiquated NTFS which needs defrag tools to be preposterous. Most enterprise level servers running on xfs or jfs or ext need no defragmenting, same is not the case with Windows where online defragmenters like PD, DK are big money. Try doing a huge file transfer of couple of gbs of files at one go. Then try accessing them, you will see a definite slow down. run a defragger and the speed picks up.

This windows mentality of frequent defrags requirement has been done to death and yet it keeps rearing its ugly head from time to time. Since the explanation is BS to you, I guess everything in Linux world is the same for you.

---

### Post by Gen2ly on 2009-06-15
MS's defragmenter also includes an optimizer too which is why I think it's so popular in Windows.  It prioritizes files that are used the most at the beginning of the disk (bootup files, most used programs...).  So while a defragmenter isn't necessary, alot of people would like to be able to optimize their hard disks.

---

### Post by rocket777 on 2009-06-15
> **Arup said:**
> 
This windows mentality of frequent defrags requirement has been done to death and yet it keeps rearing its ugly head from time to time. Since the explanation is BS to you, I guess everything in Linux world is the same for you.

I read the article you mention and all it says is that ext3 places new files more spread out on the disk, so there's room at the end of allocated disk space to extend files. But allocation granularity in other systems (minimum contiguous size of a section) likely handles this. Add a few bytes to a file and it won't need to extend the file anyway. 

Well, that's not the issue with my fragmentation problem. I haven't been able to figure out what exactly is going on here (the strace's are just too complicated for me to unravel).  I end up with a severely fragmented file every 10-20 times I run the program. 

This means every week or so I have to manually defragment this file. If I don't, performance drops from 40mb/sec to 3mb/sec. It means that startup takes 3 or 4 minutes instead of 10-20 seconds.

Whatever it's other merits, I've come across some sort of pathological ext3 case.  Maybe it's doing little shrinks and expands many times since this file is a copy of all the virtual machines memory - used to come out of a state of hibernation. Could it be a sparse file? I don't even know if ext3 has such a file type. Can one deallocate blocks of a file in the middle? That could explain things - if it was constantly doing the equivalent of malloc/free on an image of memory contained in a file and each new allocation was at a new spot on the disk.

All I know is that the same activity on NTFS does not cause this problem - but I can't even be sure that the version of vmware running on windows uses exactly the same allocation algorithm.  Unfortunately, the folks at vmware are as disinclined to view this as a problem as are the folks here that claim defragmentation is never needed or at best only required when a program is doing crazy things. Blame the user!

Doctor, my file keeps getting fragmented when I do this - well don't do it then. Vmware folks tell me simply don't use this capability and don't try to come up from hibernation but simply reboot the VM each time. They claim the problem is ext3, and ext3 folks claim the problem is vmware. I'm stuck in the middle.

---

### Post by ascariz on 2009-07-18
i think we do need defragmenter in linux.
i made a fat32 partition in ubuntu and after a long time, my sytem become slow. i mount my hard disk at windows and defrag the partition, my ubuntu become normal again after boot. so, there is an effect of defragmentation in ubuntu.
I found one software that can defrag the whole drive, folder and files.
The software is Power Defragmenter. You can find it here
[http://www.softpedia.com/get/System/...agmenter.shtml](http://www.softpedia.com/get/System/...agmenter.shtml)
Of course you need Wine to run it. So, install wine first ok.
After Power Defragmenter installed, when you run it, it will ask to download contig from windows. you need to put the contig in the same folder of Power Defragmenter.
I compressed the complete Power Defragmenter and you can run it just like portable.
you can download it here..
[http://www.mediafire.com/download.php?jwjzzz1mdnw](http://www.mediafire.com/download.php?jwjzzz1mdnw)

---

### Post by blueridgedog on 2009-07-18
> **ascariz said:**
> i think we do need defragmenter in linux.
i made a fat32 partition in ubuntu and after a long time, my sytem become slow.

Most of the defragmenting discussion surrounds Linux native file systems, such as ext2, ext3 and ext4.

---

