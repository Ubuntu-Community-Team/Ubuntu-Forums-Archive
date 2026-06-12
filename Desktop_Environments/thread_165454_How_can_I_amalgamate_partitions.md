---
title: "How can I amalgamate partitions?"
date: 2006-04-24
forum: Desktop Environments
---

### Post by jimw on 2006-04-24
The local Linux guru, when he was over to help me get my printer working, noted that I had  two extra swap partitions, neither of them accessible.  This is aside from the "normal" swap partition.

I'm having a little trouble keeping enough free space on the home partiton.  Is there some way to amalgamate these two partitions into my "home" partition without destroying data?

JimW

---

### Post by Herman on 2006-04-24
Hello, JimW, You should be able to use your favorite partitioning software such as GParted, QTParted, or DiskDrake or whatever you like to make changes to your partititions. I would just delete the two un-needed swap areas and then  re-size your other partition to fill up the resulting free space.
There is a catch though, regardless of what software you use, Linux partitions tend to be fixed and un-moveable at the left-hand end (the beginning or 'start' of the partition), but you can resize them from the 'end' or which appears to the right in most graphic partitioning software displays. So if your two extra swap areas are to the right of the partition you want to re-size larger it will be simple. If they happen to be to the left, or towards the beginning of the disk from it, it could be a little more of a challenge.
If you need specific help, please post a copy of the results you receive after entering the following code in a terminal: ```
sudo fdisk -l
``` Or, if you have GParted or QTParted installed, ('Applications', Add Applications','System tools'), you could post a screen shot of your partitions as seen in either of those. 
A partitioner that runs from a Live cd is normally easier to use for the actual re-sizing work though. 
:D Regards, Herman :D

---

### Post by jimw on 2006-04-24
Thanks, Hermann,

I've just installed both GParted and QTParted.

GParted seems the easiest one to work with (got the biggest window showing me exactly what's where.)

The output of sudo fdisk -l is:


Disk /dev/hda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         638     5124703+   b  W95 FAT32
/dev/hda2            1332        4870    28427017+   5  Extended
/dev/hda3             639        1331     5566522+  83  Linux
/dev/hda5            1403        1465      506016   82  Linux swap / Solaris
/dev/hda6            1466        4870    27350631   83  Linux
/dev/hda7            1367        1402      289107   82  Linux swap / Solaris
/dev/hda8            1332        1366      281074+  82  Linux swap / Solaris

Partition table entries are not in disk order

I'm not sure why it says those swap ones are Solaris; I used to run Mandrake, and perhaps that's the best guess Ubuntu can come to as to their provenance.

Sorry, I can't put in a copy of the Gparted Screenshot.

Thanks again, 

JimW

---

### Post by syg00 on 2006-04-24
Let's guess that your /home is on /dev/hda6.
If so, there is nothing (easy) you can do safely.

If t'was me I'd delete all 3 swaps (will give you a contiguous free area at the beginning of the extended). Then recreate a single swap of the desired size, then create another partition to use as a mountpoint under /home - say /home/jim/mp3s.
Mount that, and put all the relevant data there, freeing up the other (old) /home somwhat.

Simple, safe, and easy to change later should the need arise.
(and yes, Linux will happily run without a swap while you do this - unless you are ***real*** short of storage).

---

### Post by Herman on 2006-04-25
Hi, JimW,  I re-arranged you sudo fdisk -l into disk order and analysed it by pasting it to a gedit  text editor page. I think it looks okay to me, your three small swap areas only add up to about 0.85 of a GB. It wouldn't be worth your trouble to try to do anything for just that small amount of space, and 0.85 Gb would be a nice size for a swap area anyway. It won't matter that there are three instead of just one. I'd be happy the way it is and try to think of some other way to make more room, like either removing some data or adding another hard disk or something like that.
Sorry, but that's honestly my best advice for your situation, Regards, Herman. :D

EDIT: Presuming hda6 is your /home partition, if not, let me know and I'll have another look at it then and see what you can do.

---

### Post by syg00 on 2006-04-25
Didn't do the maths - but now you mention it, I agree.

---

### Post by jimw on 2006-04-25
Thanks again, Herman;

I've actually got plenty of room on my hd altogether, just not enough room in the home space.  And it seems that the only way to free up more would be by backing everything up, then to slate and reinstall, allowing much more room for the home section this time.

This may be a problem, since burning batches of my files onto cd is difficult, because I get an "invalid file name," which means sorting the whole mess of them to see just where the invalid file name is.

Thanks again,

JimW

---

### Post by Herman on 2006-04-26
Hi, JimW, I copied and pasted your sudo fdisk -l onto a text editor (gedit) page in order to re-arrange it so I can analyse it easier for you. Here's what, it looks like to me.

Disk /dev/hda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

If 4870 cylinders is 40.0 GB, then 121.75 Cylinders = 1.0 GB

Device Boot Start End Blocks Id System
/dev/hda1 * 1 638 5124703+ b W95 FAT32..................................................                                  637 cylinders...  5.23 GB
/dev/hda3     ......639 1331 5566522+ 83 Linux                                .................................................692 cylinders...  5.68 GB   / ?
/dev/hda2         .............1332 4870 28427017+ 5 Extended
/dev/hda8         .............1332 1366 281074+ 82 Linux swap / Solaris.....................              34 cylinders....  0.28 GB
/dev/hda7              ......................1367 1402 289107 82 Linux swap / Solaris...............          35 cylinders....  0.29 GB
/dev/hda5                   ................................1403 1465 506016 82 Linux swap / Solaris.....     35 cylinders....  0.29 GB
/dev/hda6                        .........................................1466 4870 27350631 83 Linux............           3404cylinders... 27.95 GB   /home?
....................................................................................totals........................4837cylinders....39.72 GB
Partition table entries are now in disk order

I'm guessing that /dev/hda3 would be your / (root) partition , (where your operating system is installed), 5.68 GB, and /dev/hda6 would probably be your /home partitition (where all your personal files are stored).
I still think that's pretty good the way it is, but it's up to you of course, the Ubuntu philosophy states  you have the right to modify your software until it works the way you want it to.
You know, I never have been an advocate of these multiple partition installs anyway. It would be a little more efficient space-wise, to have everything in one partition, because folders have the great advantage of being able freely and readily change to the exact, perfect size you need at every instant, where partitions are fixed and rigid. There will always be some wasted space in partititions, it is unavoidable.  IMHO, all the average desktop home user needs is one partition for Ubuntu /, and one swap area. But that's just my idea, I respect that other people have their own opinions and they are perfectly entitled to. Whatever you decide to do I'll give you any help you might ask for, and so will others here.
As for the 'invalid file name' I seem to remember something like that happening to me once too. In my case it was just warning me that a file-name longer than a certian number of digits (fifteen maybe?) might be unable to be transferred to a Windows operating system, (not that that's very important), but all I did was shorten a few of my longer  file-names. Will that help?
All the best with it anyway, Regards, Herman. :D

---

### Post by louis_nichols on 2006-04-26
I would just format the extra swap partition as ext3 and mount it in a directory under my home partition.

---

### Post by jimw on 2006-04-29
Thanks, everybody, for your help and suggestions.  

I rather agree about putting everything (except windows) on one partition.  I may have gotten an impression that Ubuntu "insisted" I put "home" on a separate partition, but as still much of a newby, I may have been taking a suggestion for a requirement.

On Sunday, when I have some free time, I'm going to reinstall Ubuntu.  If possible, I'm going to do it by formatting everything but the windows partition, and going at the whole thing again.

Is it feasible to format all the partitions but the one?  I'd prefer not to have to go to the fuss of installing Windows all over again as well.

Thanks again,

JimW

---

### Post by louis_nichols on 2006-04-29
[QUOTE=jimw]
Is it feasible to format all the partitions but the one?  I'd prefer not to have to go to the fuss of installing Windows all over again as well.

Thanks again,

JimW[/QUOTE]

Sure it is possible! It's just that you'll have to format every partition you are intersted in one-by-one and leave the one with wndows alone.

Actually, there's an easier way. You can instruct the installer to mount your current root partition as / again and format it. That would be the easiest way, I think.

---

### Post by Herman on 2006-04-29
Well it doesn't really matter what you do as long as you're having fun. :D
Yes, if it was me and I really had to get that extra bit of hard-disk space for whatever reason, I'd just use the Ubuntu installer's partitioner to delete all the partitions except for the Windows one. You'll then have a Windows partition and a lot of free space. I'd just let the Ubuntu partitioner automatically partition the free space. 
You'll get back maybe a couple of CD-ROM's worth or half a DVD's worth of hard-drive space maybe, I'd estimate. To my simple logic it would make more sense to just copy some data to a DVD and delete it off my hard-disk, that would save a lot of work. On the other hand I've had lots of fun deleting and re-installing just for the heck of it plenty of times and it hasn't hurt me at all, except it has taken up some of my time. You'll end up with a slightly better (in my opinion) set-up with a single partition (plus swap) install. I guess it really depends on how much you enjoy re-installing and trying to make your system absolutely the way you like it. That's part of the fun of computers I guess. They're a lot cheaper to modify and personalise than cars and trucks or houses. :D All the best with it, from Herman. :D

---

### Post by jimw on 2006-05-01
Okay, I did the big nasty thing.

Took me upwards of an hour to put in all the updates.

Took even longer for me to get my newsgroups set up (Not Ubuntu, just a bunch of writing-stuff off sff.net)

I now have a minimum of partitions.  1 Fat32, 1 swap, and 1everything else.

Now I go through all my correspondence to you people and see how to set up things the way I wanted them.

I'm having to use the Official (not the Ubuntu) version of OpenOffice  This means I have to look up the place where someone tells how to do the alien trick.

Thanks everybody for answering my questions, and I'm looking forward to having more in the future.

Jimw

---

