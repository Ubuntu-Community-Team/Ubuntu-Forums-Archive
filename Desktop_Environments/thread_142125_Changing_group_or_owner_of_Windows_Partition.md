---
title: "Changing group or owner of Windows Partition"
date: 2006-03-09
forum: Desktop Environments
---

### Post by FIONEX on 2006-03-09
Sorry to be asking this but the search I tried didn't help.  I'm trying to copy files directly to my C drive but I can't unless I sudo or gksudo nautilus.  It's starting to get on my nerves so I thought that I can change the permissions.  I tried to change permissions with and without sudo, but both didn't work.  Any ideas?  Or am I going about this the wrong way?

---

### Post by Sutekh on 2006-03-09
What is the format of the filesystem?  

If it is NTFS you should not attempt to write to the disc.  The NTFS write capabilities of Linux are not mature/stable.  

If it is formatted FAT32 then yes you can copy files over, but you will need to tweak your settings a little.

Follow this link to setup your Windows partitions properly to allow you access (read only if its NTFS though).

[http://http://www.psychocats.net/linux/mountwindows.php]("http://http://www.psychocats.net/linux/mountwindows.php")

Aside: You won't be able to change permissions of a Windows filesytem because they are not compatible with Linux style permissiosns.

---

### Post by FIONEX on 2006-03-14
HMM?  I dont get it, or maybe you don't get me.  I want to be able to write files directly to my C and D drive without having to do gksudo nautilus.  I'm fairly confident with all the windows files and couldn't care less if they all got fried, so I need to be able to access them without having to entery a password every time.

---

### Post by Sutekh on 2006-03-14
That link will show you how to access your files.  No gksudo nautilus, no password required.

If your C and D drive are formatted FAT32 then you will be able to read, write and execute files on them.  

If they are formatted NTFS you won't be able to write to them, NTFS write capability is not supported in Linux yet.  If you are set on doing this then have a look around for a program called [Captive NTFS]("http://en.wikipedia.org/wiki/Captive_NTFS").  There are no guarantees and its very likely that writing to NTFS could damage the data/partition beyond repair.

---

### Post by FIONEX on 2006-03-15
Thx for your help.  I wasn't sure what that link was talking about because all my drives were mounted and easily accessible.  Then I realised that my drives were mounted with different options than the ones found at that link.

For those who find this thread by search:
Change the parameters for each windows partition in "/etc/fstab" from "defaults" to "iocharset=utf8,umask=000".  I think that's what allows universal read and write to the drive.

---

### Post by mozetti on 2006-03-15
Just to beat a dead horse ...

I don't think you're grasping what Sutekh was saying about NTFS. Hopefully your partitions aren't NTFS if you're dead set on writing to them from Linux. If you try to write to an NTFS partition, there is a good chance you will corrupt it. That means you'll need to re-install Windows, and replace any files that were on the partition. Basically, it'll be fried. Happened to me.

---

### Post by FIONEX on 2006-03-15
LOL, I do understand. My partitions aren't NTFS because I don't believe in that file partition format :P.  I've always converted my partitions to FAT32.

---

### Post by rquint on 2006-03-15
One problem not solved by editing fstab is permissions on a FAT32 partition on an external or removable drive.  Has any solved that problem?

---

### Post by FIONEX on 2006-03-15
I don't know why that would be any different from a regular drive since it's just a mountable device.  However, I also would like to know the answer kuz that would affect MP3 players and cameras, etc.  Right?

---

### Post by deathbyswiftwind on 2006-03-15
maybe this is a dumb question but after formatting my hd to fat32 and making it mount correctly and stuff it will not show up in windows anymore. Is that supposed to happen?

---

### Post by Sutekh on 2006-03-15
[QUOTE=FIONEX]For those who find this thread by search:
Change the parameters for each windows partition in "/etc/fstab" from "defaults" to "iocharset=utf8,umask=000". I think that's what allows universal read and write to the drive.[/QUOTE]
Yep the umask allows read, write and execute access to the drive, for the owner, owning group and everyone else. 

Should you ever wish to change the umask to restrict the access, check out this link

[Gentoo Wiki - HOWTO Mount Windows Partitions]("http://gentoo-wiki.com/HOWTO_Mount_Windows_partitions_(DOS,_FAT,NTFS)")

Also check out the section on uid, gid aswell.  There's some good stuff.

[QUOTE=FIONEX]LOL, I do understand. My partitions aren't NTFS because I don't believe in that file partition format :P.  I've always converted my partitions to FAT32.[/QUOTE]
Okay well no worries there with FAT32.  

I wasn't assuming that you were using NTFS partitions, I just had more to say on them as opposed to FAT32 partitions.

But I'm glad that its all working now.

[QUOTE=FIONEX]
I don't know why that would be any different from a regular drive since it's just a mountable device. However, I also would like to know the answer kuz that would affect MP3 players and cameras, etc. Right?[/QUOTE]
Yes you are right.  

If its a mountable/removable device, then you should be able to mount it.  

I have mounted my USB pen drives, digital camera, MP3 player all using a similar method.


[quote=rquint]
One problem not solved by editing fstab is permissions on a FAT32 partition on an external or removable drive. Has any solved that problem?[/QUOTE]
Sure by editing the fstab.  Where do your problems stem from?  

To start is the USB drive recognised when you plug it in?

Try this code, from a terminal with the USB unplugged
```
tail -f /var/log/messages
```
then plug in the USB and note the message that appear.

If it is recognised, then post the output of ```
sudo fdisk -l
``` and ```
cat /etc/fstab
```
So we can see whats going on.


[quote=deathbyswiftwind]
maybe this is a dumb question but after formatting my hd to fat32 and making it mount correctly and stuff it will not show up in windows anymore. Is that supposed to happen?[/quote]
No that shouldn't happen.  Windows should be able to see the partition.

How did you format the partition?  Can you double check that it is FAT32?

In Windows try opening up Computer Management (its somewhere in Control Panel, Administrative Tasks maybe?) and check Disk Management.  Can you see the partition there?  It may need a drive letter assigned to it.

That's all I can think of for the moment.

---

### Post by FIONEX on 2006-03-16
Umm well you probably skipped something because that almost NEVER happens with windows.  You gotta hand it to Bill Gates, his operating system does everything for you.  Basically, when you convert a partition to FAT32, you're not necessairly formating it because you can convert a partition from NTFS to FAT with your data remaining on the drive.  Also, windows partitions must be formatted before they can be used.  So if you deleted an old partition and created the new FAT32 partition in its place, you must explicitly format it after you're done.  Else, windows will not detect it.  That's the most likely cause of your problem.

---

### Post by deathbyswiftwind on 2006-03-16
Okay I figured out what I was doing. Stupid me when I formatted my 80 gig hard drive to fat32 with gparted I made it all one partition so of course windows wouldnt assign it a letter (yet again linux shows a positive side) anyways now that I have split it up into chunks (within windows using my data tools) I cannot  make my partitions writeable. I have 3 different partitions on this drive MP3, Nikki, Rob. I want them to mount them all to be writeable. Before when I added it to my fstab linux named the drive sda1. How do I figure out what it is now? As well as what do I add to my fstab now?

Here is what I had so far
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1 /media/mp3 vfat user,rw,umask=000 0 0
/dev/sda2 /media/rob vfat user ,rw,umask=000 0 0
/dev/sda3 /media/nikki vfat user,rw,umask=000 0 0

I dont know if the /dev/ name is write but it doesnt work my permissions for each directory are 700 Ive tried switched to sdb and sdc but nothing works.

---

### Post by Sutekh on 2006-03-16
[QUOTE=deathbyswiftwind]Before when I added it to my fstab linux named the drive sda1. How do I figure out what it is now?[/QUOTE]

Use this command to list the partitions and the /dev/ locations
```
sudo fdisk -l
```

Then I would use these lines to mount the partitions (replacing the <part#> with the correct locations)
```
/dev/<part1>   /media/mp3     vfat   iocharset=utf8,umask=0000   0   0
/dev/<part2>   /media/rob     vfat   iocharset=utf8,umask=0000   0   0
/dev/<part3>   /media/nikki   vfat   iocharset=utf8,umask=0000   0   0
```

Then remount the partitions, without rebooting, using
```
sudo mount -a
```

---

### Post by deathbyswiftwind on 2006-03-16
[QUOTE=Sutekh]Use this command to list the partitions and the /dev/ locations
```
sudo fdisk -l
```

Then I would use these lines to mount the partitions (replacing the <part#> with the correct locations)
```
/dev/<part1>   /media/mp3     vfat   iocharset=utf8,umask=0000   0   0
/dev/<part2>   /media/rob     vfat   iocharset=utf8,umask=0000   0   0
/dev/<part3>   /media/nikki   vfat   iocharset=utf8,umask=0000   0   0
```

Then remount the partitions, without rebooting, using
```
sudo mount -a
```[/QUOTE]

Alright sweet thanks now I can write to them. One question though how would I change the permissions for every user to be able to write to them cause as it stands the permission for the owner "rob" is read/write/execute while the group and others have nothing. So permission reads 700

Sorry about all of this Ive just never tried to use the same drive for linux and windows before

---

### Post by Sutekh on 2006-03-16
That umask=0000 should allow everyone to have read, write and execute permissions.

Have you tried to write to the partitions logged in as a different user?

---

### Post by deathbyswiftwind on 2006-03-17
Alright well I created another account and sure enough when I login with it it tells me I am the owner with all permissions. Thank you all very much for your patience and help

---

