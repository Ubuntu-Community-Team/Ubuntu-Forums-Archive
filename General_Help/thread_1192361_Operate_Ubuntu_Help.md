---
title: "Operate Ubuntu? Help?"
date: 2009-06-20
forum: General Help
---

### Post by idk1333 on 2009-06-20
I am really new to Linux. I just dual boot Linux Ubuntu 9.04 and Window Vista two days ago. And i'm having couple of problems, i did tweaked around the web, but i still can't find a direct solution for my problems.

1st problem) I can't run/open Firefox, aMSN on Ubuntu 'anymore'.
This problem occurred right after i perform "sudo apt-get install ubuntu-restricted-extras" in > Terminal.

Don't bother telling me to install other web browsers and messengers. The result will be the same, i still can't open any of them. The task will appear on the bottom panel, after a few minutes it will dissapear and nothing will happen.

But i don't have any problems opening music files or photos, videos etc.

2nd problem) I can't download and install all of my updates, because it said, "Not enough memory on '/' drive".

Well, i'm currently using 70GB on my Vista C: drive and i still have 30GB unallocated drive.

Can i transfer those memory onto Ubuntu "/" drive?
how?

3rd question) All my preferences and changes will be set to default after i restart my computer. Why won't Ubuntu save any of my changes?.

---

### Post by merlinus on 2009-06-20
If you are running out of space on your ubuntu install, this could be the cause of many of your problems.

Run this command in a terminal and post the results:

```

df -h

```

That will give an idea of your system resources.  Also, how much RAM do you have?

---

### Post by ad_267 on 2009-06-20
Yeah it's likely that your problems are due to running out of space. You can us the Ubuntu live CD to run gparted, a partition editor, and resize your Ubuntu partition to take up that space. If you post the output of "sudo fdisk -l" we can get a better idea of what your hard drive layout is like.

---

### Post by idk1333 on 2009-06-20
> **merlinus said:**
> If you are running out of space on your ubuntu install, this could be the cause of many of your problems.

Run this command in a terminal and post the results:

```

df -h

```That will give an idea of your system resources.  Also, how much RAM do you have?

Well sir, my "df -h" results:-

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.3G     0 100% /
tmpfs                1003M     0 1003M   0% /lib/init/rw
varrun               1003M   96K 1003M   1% /var/run
varlock              1003M  4.0K 1003M   1% /var/lock
udev                 1003M  180K 1003M   1% /dev
tmpfs                1003M   84K 1003M   1% /dev/shm
lrm                  1003M  2.4M 1000M   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M   16K 1008K   2% /tmp
/dev/mmcblk0p1        243M  177M   67M  73% /media/disk
/dev/sr0              4.4G  4.4G     0 100% /media/cdrom0
/dev/sda2              69G   36G   34G  52% /media/disk-1

I would like to transfer/use my extra 30GB on Ubuntu OS. I meant to install Ubuntu on that drive, infact, i shrinked 30GB of my local C: drive just for Ubuntu, something must've got messed up during the installation. During the installation, i was prompt with three questions,

 1) (something, something) Install side by side and you will be promt each time you boot.
2) (something, something) Replace the whole hard drive.
3) Manually specify (something, something) 

I choosed option number one, is that the right choice?

By the way, i've 2GB RAM on my Vaio notebook.
Side note: I'm not having any problems connecting to the internet, or booting up Vista and Ubuntu.
I can run Firefox on Ubuntu if i run this command on > Terminal "sudo firefox -i-safemode"

I can only open firefox 'once' (in safe mode), if i closed my browser, i can't rerun firefox, even in safe mode. I would have to restart.

---

### Post by jocko on 2009-06-20
> **idk1333 said:**
> Well sir, my "df -h" results:-

Filesystem            Size  Used Avail Use% Mounted on
[COLOR=Red]/dev/sda5             2.3G  2.3G     0 100% /[/COLOR]
tmpfs                1003M     0 1003M   0% /lib/init/rw
varrun               1003M   96K 1003M   1% /var/run
varlock              1003M  4.0K 1003M   1% /var/lock
udev                 1003M  180K 1003M   1% /dev
tmpfs                1003M   84K 1003M   1% /dev/shm
lrm                  1003M  2.4M 1000M   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M   16K 1008K   2% /tmp
/dev/mmcblk0p1        243M  177M   67M  73% /media/disk
/dev/sr0              4.4G  4.4G     0 100% /media/cdrom0
/dev/sda2              69G   36G   34G  52% /media/disk-1

I would like to transfer/use my extra 30GB on Ubuntu OS. I meant to install Ubuntu on that drive, infact, i shrinked 30GB of my local C: drive just for Ubuntu, something must've got messed up during the installation. During the installation, i was prompt with three questions,

 1) (something, something) Install side by side and you will be promt each time you boot.
2) (something, something) Replace the whole hard drive.
3) Manually specify (something, something) 

I choosed option number one, is that the right choice?

By the way, i've 2GB RAM on my Vaio notebook.
Side note: I'm not having any problems connecting to the internet, or booting up Vista and Ubuntu.
I can run Firefox on Ubuntu if i run this command on > Terminal "sudo firefox -i-safemode"

I can only open firefox 'once' (in safe mode), if i closed my browser, i can't rerun firefox, even in safe mode. I would have to restart.

As you can see in your output from "df -h", your "/" partition is full. That means no program that needs to write to the hard drive will run, which is the cause of all your problems.
If you have empty space left on your hard drive, boot the computer from a live cd and go to System --> Administration --> Partition editor.
You should be able to use that to increase the size of your ubuntu partition.

---

### Post by idk1333 on 2009-06-20
> **ad_267 said:**
> Yeah it's likely that your problems are due to running out of space. You can us the Ubuntu live CD to run gparted, a partition editor, and resize your Ubuntu partition to take up that space. If you post the output of "sudo fdisk -l" we can get a better idea of what your hard drive layout is like.

Here's the results:-

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9c77b9ed

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1171     9398272   27  Unknown
/dev/sda2   *        1171       10095    71683072    7  HPFS/NTFS
/dev/sda3           10096       10420     2610562+   5  Extended
/dev/sda4           10421       14594    33519616    7  HPFS/NTFS
/dev/sda5           10096       10398     2433816   83  Linux
/dev/sda6           10399       10420      176683+  82  Linux swap / Solaris

Disk /dev/mmcblk0: 254 MB, 254803968 bytes
16 heads, 32 sectors/track, 972 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1         972      248781+   6  FAT16


Well sir, i'm not quite sure what do you meant by "Ubuntu live CD". I downloaded  Ubuntu 9.04 two days ago from ubuntu.com. Then, i burned the ISO files onto an empty DVD disc. So, i'm gonna assume that is my Ubuntu live CD.. correct?

I'm able to access gparted, and partition editor on my Ubuntu OS w/out using any disc, is that method different from what you're trying to say?

Also, as i stated my Partitions above, noticed that i have 30GB unused hard drive in NTFS format.
Now, I'm trying to install Ubuntu on that hard drive. But i don't really know how. 

Should i boot into Vista. Admistration Tools > Computer Management > Disk Management
And remove two partitions that belongs to ubuntu, but then i can't boot into Vista..

Should i reinstall Ubuntu or what?


Sorry if i am asking rather stupid questions, it's just i am really new with all these Ubuntu, Partitions, Dual boot. etc

---

### Post by nmaster on 2009-06-20
I don't want to sound like a jerk, but you really should have learned more about partitioning and ubuntu in general before taking this leap.  I would suggest wubi.  I've actually been wubi for about a month and a half and I still plan on using it for the rest of the summer before I actually install Ubuntu.  This is most likely an over conservative approach, but I don't want to mess around too much since I need my computer for the research I'm doing at the moment.

Read these. Then search the forums to read about other people's experiences installing Ubuntu.
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
  [http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)
[http://www.tomshardware.com/reviews/ubuntu-linux-guide,2293.html](http://www.tomshardware.com/reviews/ubuntu-linux-guide,2293.html)

I'm sorry for the lecture, but using Linux effectively requires a lot of learning and its not something that I've approched lightly.  I haven't had lots of problems making the move, and its because I read and read and read.  in fact, I don't allow myself to use Ubuntu at the lab anymore because all the learning was distracting me from getting work done!

If you don't find a solution, you may have to just remove ubuntu.  If this is case, look into wubi.  Unless you are in dire need of hibernate, its great.

Good luck.

---

### Post by jocko on 2009-06-20
> **idk1333 said:**
> Well sir, i'm not quite sure what do you meant by "Ubuntu live CD". I downloaded  Ubuntu 9.04 two days ago from ubuntu.com. Then, i burned the ISO files onto an empty DVD disc. So, i'm gonna assume that is my Ubuntu live CD.. correct?Correct.

> **idk1333 said:**
> I'm able to access gparted, and partition editor on my Ubuntu OS w/out using any disc, is that method different from what you're trying to say?You have to do it from a live cd, as you can't edit a partition that is in use.


> **idk1333 said:**
> Also, as i stated my Partitions above, noticed that i have 30GB unused hard drive in NTFS format.
Now, I'm trying to install Ubuntu on that hard drive. But i don't really know how. 

Should i boot into Vista. Admistration Tools > Computer Management > Disk Management
And remove two partitions that belongs to ubuntu, but then i can't boot into Vista..No, boot the live cd, use gparted to first delete the empty 30Gb ntfs partition and then resize the ubuntu partition to take up all the empty space.
Or, if you haven't got anything important in your ubuntu partition, this is probably both quicker and easier:
Use the live cd to reinstall ubuntu, but during the partitioning make sure you set up the partitions manually to:
1. Delete both the empty ntfs partition and the too small ubuntu partition.
2. Make a new ext3 or ext4 partition to take up all the empty space, and make sure it's used as "/" (root file system).
3. Also make sure the swap partition is set to be used as swap.

---

### Post by ad_267 on 2009-06-20
It looks like your 30 GB of unallocated space is before your Windows partition, so it won't be so easy to just resize your Ubuntu partition. Instead you could move your Ubuntu partitions to where that 30GB of unallocated space is at the moment and then resize it to take up that space. Be aware that moving a partition can take quite a long time though.

If you're unsure of what to do you could post a screenshot from the partition editor and we'll see if we can explain it using that.

---

### Post by idk1333 on 2009-06-20
> **jocko said:**
> Correct.

You have to do it from a live cd, as you can't edit a partition that is in use.


No, boot the live cd, use gparted to first delete the empty 30Gb ntfs partition and then resize the ubuntu partition to take up all the empty space.
Or, if you haven't got anything important in your ubuntu partition, this is probably both quicker and easier:
Use the live cd to reinstall ubuntu, but during the partitioning make sure you set up the partitions manually to:
1. Delete both the empty ntfs partition and the too small ubuntu partition.
2. Make a new ext3 or ext4 partition to take up all the empty space, and make sure it's used as "/" (root file system).
3. Also make sure the swap partition is set to be used as swap.

Well, as i can see, there's three solutions, and i think i'll go with this one:-

> boot the live cd, use gparted to first delete the empty 30Gb ntfs partition and then resize the ubuntu partition to take up all the empty space

---

### Post by idk1333 on 2009-06-20
> **neal.m.master said:**
> I don't want to sound like a jerk, but you really should have learned more about partitioning and ubuntu in general before taking this leap.  I would suggest wubi.  I've actually been wubi for about a month and a half and I still plan on using it for the rest of the summer before I actually install Ubuntu.  This is most likely an over conservative approach, but I don't want to mess around too much since I need my computer for the research I'm doing at the moment.

Read these. Then search the forums to read about other people's experiences installing Ubuntu.
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
  [http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)
[http://www.tomshardware.com/reviews/ubuntu-linux-guide,2293.html](http://www.tomshardware.com/reviews/ubuntu-linux-guide,2293.html)

I'm sorry for the lecture, but using Linux effectively requires a lot of learning and its not something that I've approched lightly.  I haven't had lots of problems making the move, and its because I read and read and read.  in fact, I don't allow myself to use Ubuntu at the lab anymore because all the learning was distracting me from getting work done!

If you don't find a solution, you may have to just remove ubuntu.  If this is case, look into wubi.  Unless you are in dire need of hibernate, its great.

Good luck.
Well honestly, i've did my research on Ubuntu and Partitioning before i started the installation. I managed to learned and grasped the basic concept of the idea/method. 

But in this case, i guess i was distraught/confused lol.  
I just figured out how to connect to the internet via wvdial yesterday, because Ubuntu doesn't support my ISP.
Then this morning, unknown problem occurred, then the second one, and the third one and so on.
They don't even give me a chance to identify the problems lel.

---

