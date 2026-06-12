---
title: "Installation partitioning question! Please help!"
date: 2009-04-09
forum: General Help
---

### Post by Pipps on 2009-04-09
I would like to install Ubuntu into one partition using the most simple default option which is available in the system setup during the installation process. Using the 'automatic, whole disk' option.

I would also like to create a separate, second partition, where I would keep all of my personal files and documents. I know that most people prefer to use '/home' for this purpose, but I would like to try and do it my way on this occasion if you don't mind. :)

When going through the system setup procedure at installation, how should I specify that I would like to install the whole Ubuntu system on one partition, and create a separate second partition, with its own mount point, which should just be used as a separate storage drive?

---

### Post by dcstar on 2009-04-09
> **Pipps said:**
> I would like to install Ubuntu into one partition using the most simple default option which is available in the system setup during the installation process. Using the 'automatic, whole disk' option.

I would also like to create a separate, second partition, where I would keep all of my personal files and documents. I know that most people prefer to use '/home' for this purpose, but I would like to try and do it my way on this occasion if you don't mind. :)

When going through the system setup procedure at installation, how should I specify that I would like to install the whole Ubuntu system on one partition, and create a separate second partition, with its own mount point, which should just be used as a separate storage drive?

Firstly, you have no choice but to use a /home folder - is is a Linux system requirement. Whether it is in the "/" partition or on a separate partition (preferred) is irrelevent, it will still exist.

The manual partition option allows you to create as many partitions as you like for whatever purposes as you like, do a search for detailed instructions.

---

### Post by Pipps on 2009-04-10
I would still be happy to use a '/home' directory, so thank you for confirming that.

In terms of a further directory for general assorted file storage, how would I go about specifying the mount point for this, in the GParted menu during the Ubuntu installation procedure?

---

### Post by drs305 on 2009-04-10
> **Pipps said:**
> I would still be happy to use a '/home' directory, so thank you for confirming that.

In terms of a further directory for general assorted file storage, how would I go about specifying the mount point for this, in the GParted menu during the Ubuntu installation procedure?

During step 4 (Partitioning) if you choose manual partitioning, you can set up additional partitions. You would just tell the installer the type (logical/priamry), how large, the name and what format to make it.

---

### Post by fieroboom on 2009-04-10
> **drs305 said:**
> During step 4 (Partitioning) if you choose manual partitioning, you can set up additional partitions. You would just tell the installer the type (logical/priamry), how large, the name and what format to make it.

This would not be the simplest option you requested in the first post. In short, what you're asking can't really be done. You either use the fully auto partitioner (simple), or you manually set up your partitions (a little more in depth). However, even manual partitioning isn't that hard. Here's a very simplified crash-course...
Basically, you need three partitions:
1) boot
2) swap
3) root
I've done it thousands of times, and still I chant that in my head when partitioning... "boot, swap, root... boot, swap, root..." :)
First, hit the manual partition option, and it will present you with what's currently on the drive. Delete all the partitions until it only says "Free Space" (**this WILL erase all data on the drive!**).
Then, create a new primary partition. This will be the boot partition, so I usually only give it 1GB for size. Set the filesystem as ext3, and make sure the bootable flag is on, and set to mount to /boot.
Next is swap. I usually give mine 2GB of swap space, but if you have a lot of ram on a newer system, you won't need that much. So create a 2nd primary partition, make it whatever size you want (1-2GB should suffice), set the filesystem to "swap" or "swap area" (can't remember exactly what it says).
Next is the root partition, aka: /
Depending on the total size of my drive, I usually give myself at LEAST 20GB on this one. Unless you're militant about keeping your apt cache clean (and a few other maintenance chores), then it's essential to give yourself plenty of room here. Set the filesystem to ext3, and set it to mount to /
Last is your custom partition... Create a 4th primary partition, and leave the size as-is (it should automatically have the size filled in so that it consumes the remainder of the drive). Set the filesystem to ext3, and set it to mount to whatever you like. You can have it mount to /home if you want, and you'll never even notice the difference, but your entire home folder will reside on a separate partition. There's also a custom option so that you can name your own mount point such as /save if you like.
That's it in a nutshell.
:D
-Paul

---

### Post by Pipps on 2009-04-10
Sir! Thank you for the brilliant advice!

> **fieroboom said:**
> Last is your custom partition... Create a 4th primary partition, and leave the size as-is (it should automatically have the size filled in so that it consumes the remainder of the drive). Set the filesystem to ext3, and set it to mount to whatever you like. You can have it mount to /home if you want, and you'll never even notice the difference, but your entire home folder will reside on a separate partition. 
This is exactly the part which I need to understand the most! Thank you!

> **fieroboom said:**
> There's also a custom option so that you can name your own mount point such as /save if you like/
This is the task which I would really like to be able to do. Can you tell me how I should go about choosing the name of the mount point for the 4th partition?

Can I just choose any name that I like? Or must I make sure that the mount point name correlates to the name of the partition?

Thank you!

---

### Post by Zimmer on 2009-04-10
Choose a name and it will identify the disk to the system. You can mount to whatever directory you like really (though it is best to keep it separate from anything that already has a useful system purpose and might cause a stir!!)

A good place is /media (you will find your CD Rom mounts in there..)

eg. /media/mystore
The mount point name does not have to correlate to the volume name you decide on.

You are constructing a setup similar to mine.
I dual boot Vista (well, I only use Vista when I need to plug in my Line6 equipment infrequently).
I have a Vista partition an Ubuntu partition (where all Ubuntu is loaded including /home) a swap partition and the remaining space is just to store data.

My data partition is not loaded at boot using fstab, so I have installed gnome-applets and use the DISK MOUNTER whenever I need to mount the drive for use. I find that handy.

You may want to have a look at these links for further tips..
[http://ubuntuforums.org/showthread.php?t=1080374&page=2](http://ubuntuforums.org/showthread.php?t=1080374&page=2)
[http://ubuntuforums.org/showthread.php?t=1072728](http://ubuntuforums.org/showthread.php?t=1072728)

---

### Post by Pipps on 2009-04-10
Thank you, Sir!

This looks to be incredibly useful, and exactly what I need! :)

---

### Post by Zimmer on 2009-04-10
Further reading...
[http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning](http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning)
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

:)

---

### Post by fieroboom on 2009-04-10
Awesome, I'm glad we could be of assistance! And as mentioned before, yes, you can name it anything you want, so long as it doesn't interfere with a pre-existing system mount point or folder, such as /usr, /etc, /bin, and so on. I always set mine to /save, and then I have a weekly backup in cron that rsyncs /home to /save/home, as well as to my colocated server. Redundancy is always better than just keeping it somewhere else.
:D
-Paul

---

### Post by Pipps on 2009-04-11
> **Zimmer said:**
> My data partition is not loaded at boot using fstab, so I have installed gnome-applets and use the DISK MOUNTER whenever I need to mount the drive for use. I find that handy.

Hi Zimmer

I have now called my own data partition '/save'.

How can I check whether or not my own data partition is automatically mounted at boot?

Thank you.

---

### Post by drs305 on 2009-04-11
You will need to know the partition designation, so run this to get the sdXX designation. The replace every sdXX with the correct one (for example, sda3):
```

sudo blkid

```

Then backup fstab and add this line:
```

/dev/sdXX /save ext3 defaults 0 2

```

Since I already had you chown /save in the other post, that is all you should need to do. Mount it with the following. If you get no results, it's mounted on /save:
```

sudo mount /dev/sdXX

```

You can use a UUID in fstab instead of /dev/sdXX. It's actually a better idea. The format if you want to do that would be:
```

UUID=ba83d184-705e-4115-9d42-0823c698a321 /save ext3 defaults 0 2

```
using the correct UUID for sdXX, of course.

---

### Post by Pipps on 2009-04-11
Thank you for your great reply! (And for noticing my other thread!)

"sudo fdisk -l" told me that my drive called '/save' is definitely sda3.

'sudo blkid' produced the following output:
> dev/sda1: UUID="d33304f1-a492-42e1-9753-1ab1436a9409" TYPE="ext3" 
/dev/sda2: UUID="5ca3cbe9-8f3c-41a7-916d-ed3073e18e15" TYPE="ext3" 
**/dev/sda3: UUID="490ba839-9466-43d6-912a-dc1bfaa18ae5" TYPE="ext3" **
/dev/sda4: TYPE="swap" UUID="80ad69c5-bac3-4b37-ac3d-bbe49bd1b056" 
/dev/sdc1: LABEL="USB DRIVE" UUID="4A75-FD75" TYPE="vfat" 
/dev/sdd1: UUID="11402cd0-6a62-415e-9d05-f8c4955a49de" SEC_TYPE="ext2" TYPE="ext3" 


I backed up the file called fstab which was located in '/etc'.

The file currently contains the following text:

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=5ca3cbe9-8f3c-41a7-916d-ed3073e18e15 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=d33304f1-a492-42e1-9753-1ab1436a9409 /boot           ext3    relatime        0       2
[B]# /dev/sda3
UUID=490ba839-9466-43d6-912a-dc1bfaa18ae5 /save           ext3    relatime        0       2[/B]
# /dev/sda4
UUID=80ad69c5-bac3-4b37-ac3d-bbe49bd1b056 none            swap    sw              0       0


Should I now change:
> [B]# /dev/sda3
UUID=490ba839-9466-43d6-912a-dc1bfaa18ae5 /save ext3 relatime 0 2[/B]

To:
> # /dev/sda3
UUID=490ba839-9466-43d6-912a-dc1bfaa18ae5 /save ext3 **defaults** 0 2'
?

Or should I change it to:
> # **490ba839-9466-43d6-912a-dc1bfaa18ae5**
UUID=490ba839-9466-43d6-912a-dc1bfaa18ae5 /save ext3 **defaults** 0 2'

Thank you for your help and I look forward to your confirmation of how I should proceed.

---

### Post by drs305 on 2009-04-11
Everything can stay as it is.

'relatime' is inserted in automatic fstab entries, even though it is now the default.

I included 'defaults' but fstab defaults to that anyway.

The # line is a comment line. Any line in fstab that begins with a # symbol is disregarded, so leaving it as /dev/sda3 is a good reminder. One note for troubleshooting: commented lines aren't updated, so although they are good reminders they should be verified they are still correct if you have problems.

So everything should be ok, since you already chowned /save to yourself. The /save partition should mount and be owned by you when the computer boots or you run "sudo mount -a" or "sudo mount /dev/sda3".

---

### Post by Pipps on 2009-04-12
You're right - it all works perfectly from statup now!

Thank you! :)

---

### Post by Scubdup on 2009-04-17
> **fieroboom said:**
> This would not be the simplest option you requested in the first post. In short, what you're asking can't really be done. You either use the fully auto partitioner (simple), or you manually set up your partitions (a little more in depth). However, even manual partitioning isn't that hard. Here's a very simplified crash-course...
Basically, you need three partitions:
1) boot
2) swap
3) root
I've done it thousands of times, and still I chant that in my head when partitioning... "boot, swap, root... boot, swap, root..." :)
First, hit the manual partition option, and it will present you with what's currently on the drive. Delete all the partitions until it only says "Free Space" (**this WILL erase all data on the drive!**).
Then, create a new primary partition. This will be the boot partition, so I usually only give it 1GB for size. Set the filesystem as ext3, and make sure the bootable flag is on, and set to mount to /boot.
Next is swap. I usually give mine 2GB of swap space, but if you have a lot of ram on a newer system, you won't need that much. So create a 2nd primary partition, make it whatever size you want (1-2GB should suffice), set the filesystem to "swap" or "swap area" (can't remember exactly what it says).
Next is the root partition, aka: /
Depending on the total size of my drive, I usually give myself at LEAST 20GB on this one. Unless you're militant about keeping your apt cache clean (and a few other maintenance chores), then it's essential to give yourself plenty of room here. Set the filesystem to ext3, and set it to mount to /
Last is your custom partition... Create a 4th primary partition, and leave the size as-is (it should automatically have the size filled in so that it consumes the remainder of the drive). Set the filesystem to ext3, and set it to mount to whatever you like. You can have it mount to /home if you want, and you'll never even notice the difference, but your entire home folder will reside on a separate partition. There's also a custom option so that you can name your own mount point such as /save if you like.
That's it in a nutshell.
:D
-Paul


Just to let you know, Paul. This has helped me a lot too. Thanks a lot. Just one question. Your instructions are really clear but I can't see whether the root partition needs to be 'primary' or logical. Later on you say "ceate a 4th primary partition" so I would guess it IS primary, but I just wanted to check.

If it is, then none of them are 'logical', so what is 'logical' used for?

Thanks for any help.

EDIT: Not to worry - I've done some googling (like I should have done in the first place) and discovered (for the benefit of other newbs) that it doesn't really matter. Primary partitions are more straight forward but you can only have 4 and logicals should work as well but aren't quite as clearly defined as primaries. I think this might have been an issue some time ago but has ceased to be.

---

### Post by fieroboom on 2009-04-17
> **Scubdup said:**
> Just to let you know, Paul. This has helped me a lot too. Thanks a lot. Just one question. Your instructions are really clear but I can't see whether the root partition needs to be 'primary' or logical. Later on you say "ceate a 4th primary partition" so I would guess it IS primary, but I just wanted to check.

If it is, then none of them are 'logical', so what is 'logical' used for?

Thanks for any help.

EDIT: Not to worry - I've done some googling (like I should have done in the first place) and discovered (for the benefit of other newbs) that it doesn't really matter. Primary partitions are more straight forward but you can only have 4 and logicals should work as well but aren't quite as clearly defined as primaries. I think this might have been an issue some time ago but has ceased to be.

For simplicity's sake, use 4 primary partitions. If you get more proficient with it later on, and need more partitions (such as with a dual boot), then spring for the secondary partitions with logical drives. However, for the purposes of the 'crash course', 4 primaries are fine.
:D
-Paul

---

