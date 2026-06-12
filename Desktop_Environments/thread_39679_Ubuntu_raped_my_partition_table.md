---
title: "Ubuntu raped my partition table"
date: 2005-06-06
forum: Desktop Environments
---

### Post by hkl8324 on 2005-06-06
A month ago i installed Ubuntu Hoary on my machine, i find it fast, sleek and useful.

Yesterday i deleted the Ubuntu partition to make some room on my HDD b/c i have to download something 7GB large :-x 

but then problem arised

after i deleted the partition, i cannot reclaim the space of that partition with tools like 
fdisk, partition magic..... partition magic said that the partition table is damaged.

i last resort was to delete all partition on my HDD.(i am forced to delete my "My Documents" partition which contains 20GB of somewhat valuable data :roll: )

did i do something wrong?

the layout of my HDD beforce the incident is as follow:

primary partition:

/dev/hda1 (10GB, windows XP instlled, NTFS)

extented partition:

logical partition 1

/dev/hda2 (20GB, the "My Documents" partition, FAT32)-all the data was lost in this
partition :-x 

logical partition 2

/dev/hda3 (7.5GB, Ubuntu "/", ReiserFS)

logical partition 3

/dev/hda4 (500MB, linux swap)

PS:Whenever i instlled Ubuntu/FedoraCore....Partition Magic always says that the partition table is damaged. Is it a linux kernel bug or something?

thank you in advance.

---

### Post by mtron on 2005-06-06
Unfortunately, you used the wrong tools.

To restore a Windows MBR, Microsoft gives information how to do this [here](http://www.microsoft.com/resources/documentation/Windows/XP/all/reskit/en-us/Default.asp?url=/resources/documentation/Windows/XP/all/reskit/en-us/prkd_tro_ldau.asp) 

I read in some forums that partition magic (at least the last powerquest version of it) had a bug with ext3 partitions, showing the whole drive as damaged. 

That has nothing to do with the Linux kernel. It is a bug of the software in Windows you are using.

---

### Post by hkl8324 on 2005-06-06
thanks for reply

i have tried the windows boot disk to fix the MBR using fdisk /mbr so that i can boot into windows XP (i cant boot into XP beforce doing this)

but i still cant read the FAT32 partition.

PS:does MBR=partition table??? :roll:

---

### Post by nilus on 2005-06-06
[QUOTE=hkl8324]thanks for reply

i have tried the windows boot disk to fix the MBR using fdisk /mbr so that i can boot into windows XP (i cant boot into XP beforce doing this)

but i still cant read the FAT32 partition.

PS:does MBR=partition table??? :roll:[/QUOTE]
 MBR is master boot record.

You can try with QTParted (is a Partition Magic-similar software for Linux). If you download simply MEPIS Linux which is a live/installable distro, you can run qtparted to delete the ubuntu's partition.

---

### Post by SNo0py on 2005-06-06
[QUOTE=hkl8324]primary partition:
/dev/hda1 (10GB, windows XP instlled, NTFS)

extented partition:

logical partition 1
/dev/hda2 (20GB, the "My Documents" partition, FAT32)-all the data was lost in 

logical partition 2
/dev/hda3 (7.5GB, Ubuntu "/", ReiserFS)

logical partition 3
/dev/hda4 (500MB, linux swap)
[/QUOTE]Hm, for me it looks like you removed the wrong partition - every extended partition also has a device-node - in your case /dev/hda2 should be around 28GB in size and contain three logical partition (hda3-hda5)...

---

### Post by hkl8324 on 2005-06-06
[QUOTE=nilus]MBR is master boot record.

You can try with QTParted (is a Partition Magic-similar software for Linux). If you download simply MEPIS Linux which is a live/installable distro, you can run qtparted to delete the ubuntu's partition.[/QUOTE]

a can delete the Ubuntu partition, but i cant add a new partition there, even the tools in windows XP say that is a unknown error. (/dev/hda3)


when i startedup windows, windows said:
lost chain at cluster XXXXX: orphan truncated...something like that (and after 1 hour of fixing, the data in the FAT32 partition became unreadable. (/dev/hda2)

---

### Post by hkl8324 on 2005-06-06
[QUOTE=SNo0py]Hm, for me it looks like you removed the wrong partition - every extended partition also has a device-node - in your case /dev/hda2 should be around 28GB in size and contain three logical partition (hda3-hda5)...[/QUOTE]

maybe i type something wrongly...

this partitiion table is like:

primary partition:

10GB (NTFS)

extented partition: 

28GB

                             logical partition 1:
                             
                             20GB (FAT32)

                             logical partition 2:

                             7.5GB (reiserFS)

                             logical partition 3:

                             500MB (swap)

i am not familiar with the "/dev/hd..." convention, so i made it wrong above.

what i did is delete the reiserFS and swap partition to yield some unallocated space.

and use the unallocated space to bulid a new partition, but failed.

---

### Post by nilus on 2005-06-06
Download an utility to check It... if is there any error it will resolve It.
What's your hd brand?

---

### Post by hkl8324 on 2005-06-06
[QUOTE=nilus]Download an utility to check It... if is there any error it will resolve It.
What's your hd brand?[/QUOTE]

.....i know...i just "fixed" it..but the data is all gone..(the FAT32 20GB) :-x 

i posted this thread just for whining... ](*,)  



by the way, the brand of my HD is toshiba..(it is a laptop computer)

---

### Post by az on 2005-06-06
If you stick to using the installer's partitioner, you would avoid these problems.  You can boot into it to shrink, grow and move partitions around.  You need to be unmounted anyway!

In the end, it is Partition Magic that borked your system, right?

---

### Post by hkl8324 on 2005-06-06
[QUOTE=azz]If you stick to using the installer's partitioner, you would avoid these problems.  You can boot into it to shrink, grow and move partitions around.  You need to be unmounted anyway!

In the end, it is Partition Magic that borked your system, right?[/QUOTE]

maybe....

i remembered i have see something in bugzilla that Fedora Core messes the partition table, so i guess Ubuntu may. 



 ;-)

---

### Post by mmealman on 2005-06-06
[QUOTE=hkl8324]maybe....

i remembered i have see something in bugzilla that Fedora Core messes the partition table, so i guess Ubuntu may. 



 ;-)[/QUOTE]

No. There was an uncommon bug with 2.6 and disk geometry that hit Fedora Core because it was one of the bigger dists around using the new kernels. But that error was an issue where you installed FC on a system and you could no longer boot into Windows.

There's nothing in Ubuntu or Linux that was messing up your partition tables. It sounds like you were using partition magic to create partition volumes and installing within those. If you installed Linux outside of PM you wouldn't have seen that.

But then, you wouldn't have been able to resize your paritions either.

Find an old computer, throw a large hard drive into it, install Ubuntu onto it and use it as a fileserver for both Linux and Windows. Then your HD space troubles will go away.  :smile:

---

### Post by az on 2005-06-06
"But then, you wouldn't have been able to resize your paritions either."

Yes he could!

---

### Post by Seti on 2005-06-06
I betcha it was Partition Magic, because when I used to use Partition Magic it did something very similar to me once. (With logical partitions formatted ext3).

---

### Post by tread on 2005-06-06
I had a similar experience with Partition Magic and ext3, though it never bothered me since I never deleted the partition I created till the day I sold that machine, when I just used a rescue disk. But I'm wandering, what I came here to say is, ya, this happened to me too with partition magic and ext3.

---

