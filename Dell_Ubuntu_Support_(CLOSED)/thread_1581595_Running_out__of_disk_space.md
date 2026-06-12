---
title: "Running out  of disk space"
date: 2010-09-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by iluminameluna on 2010-09-24
I'm an Ubuntu newborn but have some experience w/ DOS commands and have used sudo bash commands but only copying them.

Setup: Dell OptiPlex GX270 w/ a 40G HD, 16G SanDisk USB w/ Ubuntu Live CD, 16G Kingston USB

Problem:  I decided to install Ubuntu side-by-side w/ my Win XP, SP3. I didn't  realize that I had a 16G Kingston USB stick plugged in in the back of  the box. According to Windows, there are 24G used and 13G available. I  thought that using that 13G as a partition for Ubuntu would work.

When  I went to use the Ubuntu desktop the day after the installation, it  loaded but I had a warning that I only had 282.3M of space available,  although it had not given me that warning immediately afterwards. I had  used both desktops w/out any problems

I realized as I sat there,  staring at the msg on the Ubuntu desktop, that I had removed the 16G  Kingston stick the night before. I plugged it back in, at the front this  time, and the warning went away.

I came to the conclusion that I  had somehow installed part of the Ubuntu os on the Kingston stick but  I'm not sure what part or how much of it.

I wouldn't mind just  turning the entire desktop over to Ubuntu but I'm not too sure about  just eliminating my Windows os. I live in a rural part of El Salvador  and help isn't available if I find I can't access external hd's, for  instance, that were used w/ my windows os and have no way of going back  to it. I have the Dell Windows installation disk but it's not the full  os, I don't think. Mostly, I'd like to re-install Ubuntu w/out the  Kingston drive, if possible. The alternative is to use Ubuntu w/ the  stick plugged in and resign myself to not having it available for other  uses, which might be annoying but not overly upsetting. I have 2 more.

Any help? Ideas? Suggestions?

I'd appreciate any of the above ... I include the output of df -h: w/ the Kingston USB.                     


df -h
Filesystem                Size          Used         Avail         Use%         Mounted on
/dev/sda5             8.1G  7.5G  209M  98% /
none                 1002M  300K 1002M   1% /dev
none                 1006M  412K 1006M   1% /dev/shm
none                 1006M   92K 1006M   1% /var/run
none                 1006M  8.0K 1006M   1% /var/lock
none                 1006M     0 1006M   0% /lib/init/rw
/dev/sda1              29G   23G  6.6G  78% /media/34E0614DE0611700
/dev/sdb1              12G  4.9G  6.4G  44% /media/KINGSTON

---

### Post by mikewhatever on 2010-09-24
Hi iluminameluna, you seem to have a very large installation of Ubuntu, at least for the new installation. In my experience, when just installed, Ubuntu takes about 3.4GB, while in your case, it's 7.5GB on an 8GB virtual disk. This means, you've either installed a lot of programs or have large files in your home directory. In the first case, you can free some space by deleting the cached installation packages with the following command:
```
sudo apt-get clean
```

I don't think parts of Ubuntu are installed on the USB drive; it wouldn't boot at all without the usb thrive if that was the case.

---

### Post by iluminameluna on 2010-09-25
> **mikewhatever said:**
> Hi iluminameluna, you seem to have a very large installation of Ubuntu, at least for the new installation. In my experience, when just installed, Ubuntu takes about 3.4GB, while in your case, it's 7.5GB on an 8GB virtual disk. This means, you've either installed a lot of programs or have large files in your home directory.
I did install Ubu side-by-side w/ my Win XP Pro, SP3 so I went looking at the Linux installation w/ the File Browser and this is what I found:

/media 27.4G in which Folder 34E0614DE0611700 (Win's part of the hard drive) has a total capacity of 28.7G of which 22.2G is used and free space is 6.5G. (I used the R mouse button to get to the Properties of ALL the folders in the Filesystem, one by one.)

It's the only folder that has any significant size to it.

Also, Ubu and Win are on my 40G hard drive.

Is there anything I can do that will generate a report that shows more specifically what's where and how much of it there is in my Linux installation?

> In the first case, you can free some space by deleting the cached installation packages with the following command:
```
sudo apt-get clean
```I don't think parts of Ubuntu are installed on the USB drive; it wouldn't boot at all without the usb thrive if that was the case.You're right. I got thrown by the fact that Ubu "sees" the stick at once and takes it's space and data into acct.

I did do what you suggested but it made no difference. Also, I haven't really installed anything yet on my Ubu installation. I'm still seeing how well I can manage it before I invest any time in setting it up for myself.

I'd also like your opinion as to whether I could just go over to Ubu on my system. I do have 4 80G hard drives that I use as external hd's 'cause I had 2 desktops at one point but they both died untimely deaths which is how I came to get this OptiPlex. They're my only real concern about converting. And this weird space conundrum.

Any help would be appreciated.

---

### Post by mikewhatever on 2010-09-25
Look at the output of **df -h** you posted earlier.

/media/34E0614DE0611700 - that's your Windows partition, as it is seen from Ubuntu.

/dev/sda5 8.1G 7.5G 209M 98% / - this is Ubuntu itself in a virtual disk, probably inside the Windows partition.

---

### Post by iluminameluna on 2010-09-25
Hi, forestpiskie:

I happened to read Mr. Xulu's post as I'm desperately seeking salvation. I'll post what I got after following your instructions for him.

```
sudo fdisk -l
```Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xaf5aaf5a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3747    30094736+   7  HPFS/NTFS
/dev/sda2            3747        4866     8986625    5  Extended
/dev/sda5            3747        4812     8553711   83  Linux
/dev/sda6            4812        4866      432128   82  Linux swap / Solaris


[COLOR=DarkRed]# This next is a 16G MicroCruzer I have plugged in .... sorry.[/COLOR]

Disk /dev/sdc: 16.0 GB, 16026435072 bytes
64 heads, 32 sectors/track, 15283 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000027aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       15283    15649776    c  W95 FAT32 (LBA)


```
mount
```/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jessie/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jessie)
/dev/sdc1 on /media/C3F1-8581 type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda1 on /media/34E0614DE0611700 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

[COLOR=DarkRed]I don't know if I've made things worse or not. Let me know .... :confused:[/COLOR]

---

### Post by iluminameluna on 2010-09-25
> **mikewhatever said:**
> Look at the output of **df -h** you posted earlier.

/media/34E0614DE0611700 - that's your Windows partition, as it is seen from Ubuntu.

/dev/sda5 8.1G 7.5G 209M 98% / - this is Ubuntu itself in a virtual disk, probably inside the Windows partition.

I'm confused now. A virtual disk? I did the same thing as Mr. Xulu I installed Ubu side-by-side when given the choice, w/ a multiple choice window when I start up my system; I did, however, tell it I wanted 10G for the ext4 and 3 for the swap (dba5 and dba 6, respectively) since I had ck'd Win before beginning the install to see how much free space it said was available.

Is it possible to just wipe the installation and start over?

Unlike Mr. Xulu, I hadn't noticed Ubu in the Add/Remove part of the Control Panel. And for the record, I'm running Win XP Pro, SP3 on a 40G hard drive.

Thanks, forestpiskie. You :guitar:

---

### Post by Elfy on 2010-09-25
I've moved these out to a thread of their own - it really isn't a good idea to jump in another thread unless you are completely sure you have the same issue.

Thanks for > Thanks, forestpiskie. You  but I don't really - _everyone who comes here to help does_ - mikewhatever for instance does a stirling job regularly and is the one who's been helping you ;)

I've also removed the colour formatting from your posts - please follow the CoC - this states 

> Please use color and font properties for highlighting portions of your text, and not for all of the text in your post.

---

### Post by Elfy on 2010-09-25
> Is it possible to just wipe the installation and start over?Yes it is.

If you reinstall over the top of the existing installation you will have more space - however if you do whatever it was you did before then you will soon run out of space.

Either resize the windows partition to allow more space from ubuntu or you could store more data away from the ubuntu install on other drives.

---

### Post by iluminameluna on 2010-09-25
> **forestpiskie said:**
> I've moved these out to a thread of their own - it really isn't a good idea to jump in another thread unless you are completely sure you have the same issue.

I'd been looking all over this forum and others for help and when I posted that first Reply, I honestly couldn't find where to click to start a thread of my own. The only option I felt I had in the end was to crash a thread that I thought most closely resembled an issue of my own. Thus I was posted there and w/ Mr. Xulu.

> Thanks for  but I don't really - _everyone who comes here to help does_ - mikewhatever for instance does a stirling job regularly and is the one who's been helping you ;)I was also going to thank mikewhatever. The only reason I had you to thank first was 'cause you were the last one that'd replied and it was your suggestion I was responding to. That's the only reason. I DO appreciate everyone that doesn't imply I'm an idiot, lazy or wasting everyone's time. It's happened to me more than once already and so am grateful when someone gives me constructive advice.

> I've also removed the colour formatting from your posts - please follow the CoC - this statesI apologize for not following posting etiquette but I was mostly trying to do it for my own benefit rather than to annoy anyone. I usually don't do it but at the time I was writing that post, I was trying to fight my way through a migraine. My meds hadn't quite kicked in yet and I was having trouble just distinguishing where I wanted to quote someone or define a thought clearly.

In essence, I think I managed to annoy you no end tonight. I'm sorry but I do regret the various faux pas. They weren't intentional or purposely careless. :redface:

I hear you, btw, about the re-installation of Ubu and having to make sure that I don't let the os' fight it out for the space by defining their boundaries.

However I have 2 questions:

1. When you say > Either resize the windows partition to allow more space from ubuntu [COLOR=Indigo]or  you could store more data away from the ubuntu install on other drives[/COLOR]., how does one go about doing it?

2. Those other drives I mentioned earlier, they were all setup and used under Windows environments only. If I were to migrate to a purely Ubuntu environment, would I still be able to access the data on them?

My heartfelt appreciation to anyone/everyone who's been so helpful. You're all :KS in my book!

---

### Post by Elfy on 2010-09-25
> I'd been looking all over this forum and others for help and when I posted that first Reply, I honestly couldn't find where to click to start a thread of my own.  - [http://ubuntuforums.org/showthread.php?t=1006656](http://ubuntuforums.org/showthread.php?t=1006656)
> 
I DO appreciate everyone that doesn't imply I'm an idiot, lazy or wasting everyone's time.I did assume that to be the case :) -  

> It's happened to me more than once already and so am grateful when someone gives me constructive advice.report it when it happens
> 
In essence, I think I managed to annoy you no end tonight.nope - not at all :)
> 
When you say
Quote:
Either resize the windows partition to allow more space from ubuntu or you could store more data away from the ubuntu install on other drives.
, how does one go about doing it?You need to add them to fstab - you can do it manually or there are a couple of gui apps that will do it for you - pysdm is one, ntfs-config another. Fstab details are here - [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) 

To resize you'd need to use a partition editor - there's one on the livecd - you will not be able to resize the install while it is mounted.

> Those other drives I mentioned earlier, they were all setup and used under Windows environments only. If I were to migrate to a purely Ubuntu environment, would I still be able to access the data on them?Yes  - both the two I mentioned will help you access that.

> 
I usually don't do it but at the time I was writing that post, I was trying to fight my way through a migraine. My meds hadn't quite kicked in yet and I was having trouble just distinguishing where I wanted to quote someone or define a thought clearly.My symapthy - not nice. Perhaps next time you could use colour while creating the thread and then remove the colour just prior to posting - just a thought.

---

