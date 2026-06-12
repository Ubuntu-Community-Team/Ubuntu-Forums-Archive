---
title: "[SOLVED] Changing disk partitioning layout"
date: 2009-01-01
forum: General Help
---

### Post by Belerophon on 2009-01-01
Hi.

I have a question about partitions.
I have attached a screenshot of gparted, showing my disk.
Unfortunately, due to a former XP installation, my linux partition is in the middle of two others. So, I cannot join the two other ext3 partitions into one bigger partition.

So my question is:
is it possible to backup my linux installation somehow (complete image), format my disk building a custom partition layout, and put back the linux system on the new layout? 
The objective is to get rid of those two ext3 partitions and build a single, bigger partition.

Thanks.

---

### Post by drs305 on 2009-01-01
Most important: You are considering moving every byte on your computer. Make sure you backup everything that is important before attempting this. I have found gparted, partimage and related apps highly reliable; but things happen (power loss, Murphy's law, etc).

Yes, it is possible to do what you want. You could make an image of your ubuntu partition using several different methods. I like partimage but there are others, even command line 'dd' options. With partimage, compressed it would fit on your current sda2 (maybe even uncompressed, which would be even better). You could then delete the ubuntu/sda3 partition, do your repartitioning, and create a ubuntu partition. Restore ubuntu using a partimage, systemrescue or livecd CD.

One important note: Once you have restored ubuntu the UUID of it's partition will have changed. You will have to make changes in grub and fstab to get things working correctly again.

If you use partimage and have to compress the backup there have been some users who have problems restoring single file partimage backups that are larger than 2GB, so you probably would want to break the file up into pieces of 2GB (which I believe is the default with partimage).

Of course, another option would be to move your /home partition to sda2, which would preserve most of your settings, and then reinstall ubuntu, making sure to NOT select 'format the partition' when you designate the /home partition.

---

### Post by Shpongle on 2009-01-01
Hey im lookin to partition my disk aswell so i can duel boot with ubuntu and windows, i need the windows:( for fruity loops coz wine doesnt fully support it, im using ubuntu 8.10 on my laptop and g parted wont let me split the disk to make an ntfs partition, i tried using qt parted and i got this error 

"Failed to execute child process "qtparted-root" (No such file or directory)"

i installed qtparted from the universe but its not working,

im fairly new to linux and ubuntu but i have a good concept on computers in general, 

any help is welcomed coz i dnt wanna have to reformat and reinstall ubuntu through windows:(


thanks

---

### Post by bumanie on 2009-01-01
I would firstly back up anything important - moving data around can lead to corruption. If you want to make a  clone of the disk and have a large enough external drive, I'd do a simple dd command to copy sda to sdb eg dd if=/dev/sda of=/dev/sdb It is up to you whether you think you  need a clone or whether saving important data is enough.
Then: It looks as though only the filesystem is on sda3 - if so delete it, it will become unallocated. Next slide swap, followed by sda2 to the right of the drive, thus 'moving' the unallocated space next to sda1. It then should just be a matter of extending sda1 into the unallocated space. It's a while since I've used gparted like this as I have plenty of HDD space, but if my memory serves me correctly, what I have said should work.

---

### Post by drs305 on 2009-01-01
> **DillByrne said:**
> im using ubuntu 8.10 on my laptop and g parted wont let me split the disk to make an ntfs partition, 

Some of the older versions of gparted don't support ntfs very well, if at all. The versions from the livecd work and older ones in the repositories may work if you install ntfs-progs:
```

sudo apt-get install ntfsprogs

```

I use gparted with ntfs partitions frequentsly, but understand ntfs is not a native file system for linux and messing with these partitions should normally be accomplished via windows software if it is available.

---

### Post by thomas228 on 2009-01-01
> **DillByrne said:**
> Hey im lookin to partition my disk aswell so i can duel boot with ubuntu and windows, i need the windows:( for fruity loops coz wine doesnt fully support it, im using ubuntu 8.10 on my laptop and g parted wont let me split the disk to make an ntfs partition, i tried using qt parted and i got this error 

"Failed to execute child process "qtparted-root" (No such file or directory)"

i installed qtparted from the universe but its not working,

im fairly new to linux and ubuntu but i have a good concept on computers in general, 

any help is welcomed coz i dnt wanna have to reformat and reinstall ubuntu through windows:(


thanks

Hi 
How did you install ubuntu?
It almost sounds like you installed it inside windows which will have a major effect on how people help you solve your problem

Just an observation edit: sorry about that Just read your next post and it,s obvious that you only have ubuntu on your laptop end of edit

Tom

PS  Did you try to use gparted from a livecd.? That way the installed version should be unmounted and I think that can make a differnce

Tom

---

### Post by Shpongle on 2009-01-01
thanks man , i tried that but it says it cant find the packages

if you know another partition editor that i can use i just need to be able to split the main ext and to make the new partition unformatted or ntfs and i can install xp onto the newly made partition by booting it from the disk,

---

### Post by Shpongle on 2009-01-01
> **thomas228 said:**
> Hi 
How did you install ubuntu?
It almost sounds like you installed it inside windows which will have a major effect on how people help you solve your problem

Just an observation edit: sorry about that Just read your next post and it,s obvious that you only have ubuntu on your laptop end of edit

Tom

PS  Did you try to use gparted from a livecd.? That way the installed version should be unmounted and I think that can make a differnce

Tom

hey Tom, no i have the cd,but not with me at the moment but ill try it when i go home, i installed gpated form the universe it seems to work but when i highlight the disk the options at the top just remain shaded:(

---

### Post by Belerophon on 2009-01-01
> **drs305 said:**
> Most important: You are considering moving every byte on your computer. Make sure you backup everything that is important before attempting this. I have found gparted, partimage and related apps highly reliable; but things happen (power loss, Murphy's law, etc).

Yes, it is possible to do what you want. You could make an image of your ubuntu partition using several different methods. I like partimage but there are others, even command line 'dd' options. With partimage, compressed it would fit on your current sda2 (maybe even uncompressed, which would be even better). You could then delete the ubuntu/sda3 partition, do your repartitioning, and create a ubuntu partition. Restore ubuntu using a partimage, systemrescue or livecd CD.

One important note: Once you have restored ubuntu the UUID of it's partition will have changed. You will have to make changes in grub and fstab to get things working correctly again.

If you use partimage and have to compress the backup there have been some users who have problems restoring single file partimage backups that are larger than 2GB, so you probably would want to break the file up into pieces of 2GB (which I believe is the default with partimage).

Of course, another option would be to move your /home partition to sda2, which would preserve most of your settings, and then reinstall ubuntu, making sure to NOT select 'format the partition' when you designate the /home partition.


I've been taking a look to partimage. It seems to be the solution, thanks.

But so, if I use partimage, and backup sda3 into a file, it's just a matter of doing whatever changes I want to the disk, create a new partition ext3 with "/" as mount point, and restoring the image into there. From there, I must boot with a live cd, and make the necessary changes to the fstab, grub config... (any other file??)

Correct?

Imagine I format the entire disk, will grub still boot?

---

### Post by drs305 on 2009-01-01
> **Belerophon said:**
> I've been taking a look to partimage. It seems to be the solution, thanks.

But so, if I use partimage, and backup sda3 into a file, it's just a matter of doing whatever changes I want to the disk, create a new partition ext3 with "/" as mount point, and restoring the image into there. From there, I must boot with a live cd, and make the necessary changes to the fstab, grub config... (any other file??)

Correct?

Imagine I format the entire disk, will grub still boot?

No, you would *not* create a / partition or install ubuntu. You would simply create an ext3  partition of a given size (at least as large as your original ubuntu system was using - check before you do this with the "df -h" command) and then restore the image to that partition.

You will have to reinstall grub or you can try a pretty slick trick - redesignate the new partition's UUID to the *current* partition UUID. To do this, run this command before you change anything:
```

sudo blkid

```
Record the UUID of your system partition. It would be nice to copy this somewhere you can access it later (usb thumb drive, etc) so you can copy/paste it rather than type it.

After you restore the partition, you may not be able to boot to ubuntu. Insert the liveCD, note the partition your ubuntu system is now installed on and then run this command:
```

sudo tune2fs -U <enter the OLD UUID number here> /dev/*sd[COLOR="Red"]XX[/COLOR]*

```
Example: 
sudo tune2fs -U 21726b73-6688-42c4-8ad7-087659086cc1 /dev/sda1

---

### Post by Belerophon on 2009-01-01
> You will have to reinstall grub or you can try a pretty slick trick - redesignate the new partition's UUID to the current partition UUID. To do this, run this command before you change anything:


Nice! This way is less prone to errors, as I will have to make changes in fewer places! Just change the UUID and all config files are good to go.

Thanks a lot! I'll give it a try when I get my hands on a external hard drive to store the image. I prefer to play safe, and don't use compression and just save the image as it is, directly to a external hard drive with plenty of space :)

Thanks, once again, drs305 ;)

---

### Post by Belerophon on 2009-01-03
Partimage rocks :D

I've attached the screenshot of my new partitions. I all went very well, and it was very easy.

Well, I booted with ubuntu live cd (the partition to save must be unmounted) and installed partimage. Had to enable the universe repos first.
Then, it was just a matter of running partimage, and saving the system image into a external drive, plugged in by usb.

Then I just deleted all my partitions, and created three new ones: one for the system, one for general purpose and a swap.

After this, I just ran partimage again to restore the image. Very easy.

The complicated part was to make the system boot again.

First attempt, there was a grub error. I suppose it was because the MBR information pointed to somewhere that simply didn't existed any more. I had to setup grub again (thanks drs305 for the tip) --- I boot the live cd again and used the grub console. Details can be seen in this great post:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Still this wasn't enough. The fstab file was wrong, because it had wrong UUID for the system partition. I just edited it and put the new partition UUID of the system. To find it you can use:
```
sudo blkid
```

Finally menu.lst was also with wrong information. Had to change the line:
```
root		(hd0,2)
```

and change (hd0,2) to(hd0,0). This points to which partition has the kernel I think. But this info can be found through grub console, with:
```
find /boot/grub/stage1
```

Done. My system booted again in a newly created partition. Without any data loss.

Partimage seems great to make backups. And the compression helps with this. I'll be using it to backup my entire system.

But now I am intrigued with something:
now when I run sudo blkid, I get this:
```
/dev/sda1: UUID="0428a40b-755e-4dcf-aaaf-f6cdb838b78c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="c30720e2-a581-4242-8539-d5959d77f3b5" SEC_TYPE="ext2" TYPE="ext3" LABEL="Misc" 
/dev/sda3: TYPE="swap" LABEL="Swap" UUID="37dd38e3-ce77-4efa-bcb8-8e7ed5bdfb65" 
/dev/sda4: TYPE="swap" UUID="61a73cf3-0b0c-4812-849c-88d55abdc7e1" 
/dev/sdb1: UUID="c6200950-2a97-4cb1-a1ef-6c92dfd9d980" SEC_TYPE="ext2" TYPE="ext3"
```

But my system has only 3 partitions! the sdb1 seems to be my external drive, which is no longer plugged in!? And there's two swaps????

---

### Post by drs305 on 2009-01-03
> **Belerophon said:**
> 
But now I am intrigued with something:
now when I run sudo blkid, I get this:
```
/dev/sda1: UUID="0428a40b-755e-4dcf-aaaf-f6cdb838b78c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="c30720e2-a581-4242-8539-d5959d77f3b5" SEC_TYPE="ext2" TYPE="ext3" LABEL="Misc" 
/dev/sda3: TYPE="swap" LABEL="Swap" UUID="37dd38e3-ce77-4efa-bcb8-8e7ed5bdfb65" 
/dev/sda4: TYPE="swap" UUID="61a73cf3-0b0c-4812-849c-88d55abdc7e1" 
/dev/sdb1: UUID="c6200950-2a97-4cb1-a1ef-6c92dfd9d980" SEC_TYPE="ext2" TYPE="ext3"
```

But my system has only 3 partitions! the sdb1 seems to be my external drive, which is no longer plugged in!? And there's two swaps????

One of things I find odd about blkid is that it will resort to old data. Try running it like this and see if it makes more sense. This will always give the current data and some run it like this all the time.:
```

sudo blkid -c /dev/null

```
If it is correct you can update blkid to use the new info. There is probably a way to do it with a switch from the man page but I know you can, as root, delete /etc/blkid.tab and /etc/blkid.tab.old and update it that way. They will be recreated the next time you run the command.

Congratulations on your success!

---

### Post by Belerophon on 2009-01-03
> **drs305 said:**
> One of things I find odd about blkid is that it will resort to old data. Try running it like this and see if it makes more sense. This will always give the current data and some run it like this all the time.:
```

sudo blkid -c /dev/null

```


Yes, this way it's all good.

Unfortunately though, I noticed something more serious now: someone stole my free space! lol

In my previous post, the screen shots attached (I've attached them again here) show that I had a ~29GiB system partition, and was using ~14GiB. After the whole operation, Gparted shows that I have a new partition of 34GiB (that's correct, it was the size I used to create it) but there's a odd value of ~17GiB of used space. I cannot recall using 3GiB from one moment to other.

Also, the output of discus utility is very confusing:
```
Mount           Total         Used         Avail      Prcnt      Graph
/               28.74 GB     11.58 GB     17.15 GB    40.3%   [****------]
+ib/init/rw      0.99 GB         0 KB      0.99 GB     0.0%   [----------]
/sys                0 KB         0 KB         0 KB     0.0%   [----------]
/var/run         0.99 GB       240 KB      0.99 GB     0.0%   [----------]
/var/lock        0.99 GB         0 KB      0.99 GB     0.0%   [----------]
/dev             0.99 GB       2.7 MB      0.99 GB     0.3%   [----------]
/dev/shm         0.99 GB       1.2 MB      0.99 GB     0.1%   [----------]
+onnections         0 KB         0 KB         0 KB     0.0%   [----------]
+c/volatile      0.99 GB       2.0 MB      0.99 GB     0.2%   [----------]
+media/Misc     38.76 GB     29.24 GB      9.52 GB    75.4%   [********--]
+l/security         0 KB         0 KB         0 KB     0.0%   [----------]
+infmt_misc         0 KB         0 KB         0 KB     0.0%   [----------]
+on/Private     28.74 GB     11.58 GB     17.15 GB    40.3%   [****------]
+phon/.gvfs         0 KB         0 KB         0 KB     0.0%   [----------]

```


It shows ~11.58 GiB of used space, which I believe is correct since I emptied my trash. But it says that the partition has only ~29GiB !!

How is this possible?

---

### Post by Belerophon on 2009-01-04
Seems that everything says to me that I have a partition of 28.7GiB, when I created one with 34 !!! System Monitor and Disk Usage Analyser both say that...

Can't seem to find why my free space is gone. I'll probably open a new thread about this issue.

However, after the restore of the filesystem with partimage, through the live cd, I decided to take that chance to follow an optimization guide I found on the web:
```
sudo e2fsck -fDv /dev/sda1
```

this should optimize the directory structure and be perfectly safe...can this be the source of the problems??

---

### Post by Belerophon on 2009-01-04
Moved this problem to:
[http://ubuntuforums.org/showthread.php?p=6491466](http://ubuntuforums.org/showthread.php?p=6491466)


Thanks.

---

### Post by drs305 on 2009-01-04
One avenue to explore would be how partimage's partition copying writes to the partition tables. The reported partition size of 29GB is very nearly identical to the size of the original partition you copied into your 34GB space.

caljohnsmith has done some excellent work on these forums with Testdisk in getting things restored. You can search for his posts or hopefully he can respond to your queries.

---

