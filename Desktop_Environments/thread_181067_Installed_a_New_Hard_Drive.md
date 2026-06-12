---
title: "Installed a New Hard Drive"
date: 2006-05-23
forum: Desktop Environments
---

### Post by zpro on 2006-05-23
We just installed a new hard drive, ide and set it up as slave,
however, can see the hard drive listed in the /dev/hd* 

how does one find the drive, format the drive, and mount the drive,
this drive is going to be used for is storage mp3, .pdf's files..etc.

Thanks -
:confused:

---

### Post by Ramses de Norre on 2006-05-23
```
sudo aptitude install gparted && gparted
```

Nice partition editor, use it to format the hard drive.
Then edit your /etc/fstab so the partition(s) is/are mounted on start up.

---

### Post by zpro on 2006-05-23
Thanks, I install it, and can see the hdb drive,
however, there are 4 partition on it, that have caution sign,
and no filesystem, 

HOw does one wipe the drive, and re-format, and mount
using this?

Thanks

---

### Post by Ramses de Norre on 2006-05-23
Delete the existing partitions and create new ones?

---

### Post by zpro on 2006-05-24
okay deleted the partition, using gparted
now formated fat32, how does one mount the new partition
hdb2 would be 76GB partition.

Thanks
:-?

---

### Post by u.b.u.n.t.u on 2006-05-26
This many help.

[http://www.ubuntuforums.org/showpost.php?p=1053803&postcount=8]("http://www.ubuntuforums.org/showpost.php?p=1053803&postcount=8")

---

### Post by crispy_420 on 2006-05-26
[QUOTE=zpro]okay deleted the partition, using gparted
now formated fat32,[/QUOTE]

Just me but I don't like FAT32 due to file size restrictions. You won't be able to save a file over 4GB. But that is just me.

---

### Post by clint1010 on 2006-05-26
format as fat32 if you want to share the partition with a windows system, linux will be able to read and write to the drive, linux can read, but can't write to a NTFS file system. If its just linux using the drive, ext3 is a much better idea.

---

### Post by ifokkema on 2006-05-26
[QUOTE=crispy_420]Just me but I don't like FAT32 due to file size restrictions. You won't be able to save a file over 4GB. But that is just me.[/QUOTE]

It gets worse - this won't work because Windows will not be able to read this drive. Fat32, according to microsoft, can't be bigger than 30 Gb or so. Windows will not be able to mount this drive.

Ivo

---

### Post by zpro on 2006-05-26
[QUOTE=u.b.u.n.t.u]This many help.

[http://www.ubuntuforums.org/showpost.php?p=1053803&postcount=8]("http://www.ubuntuforums.org/showpost.php?p=1053803&postcount=8")[/QUOTE]
--
Okay, I figured it out: :-D 
first: add to your link this:
created a folder called 80gb ( no hdd ) just 80gb works easier...
then click enable. ( now its there.... for access.)
look at the mout point (mine /80gb) and the device /dev/hdb   /dev/hdb2
--
Next: Launcher:-D 
First, find the folder 80gb click into it, then add it as a bookmark
second: goto bookmarks, and select it and look you will see: file:///80gb
third: create a launcher type name: 80gb Hard Drive, and down by TYPE:
select LINK: and type in What the BOOKMARK Address was: (mine: file:///80gb)
click ok, and then you will see a icon, click on and it puts you into the that folder.:-D 

Fourth:
When rebooting, I lose the the new mounted drive:
so, have to edit the /etc/fstab file: (sudo gedit /etc/fstab)
Look at the file type: you will see hda3 which is a ext3 file type:
so, all I did was to copy this:

(Mine) /dev/hdb2          /80gb           ext3         defaults,errors=remount-ro 0    1
save, and exit
--
and when I rebooted this time the hard drive mounted, and the launcher icon
work just fine.

-- Now please note: I'm learning fast, but AM NOT a LINUX GURU.
SO, ANYONE, please correct this, or add to this, and make this a PIN to the message board for ALL.

and last: I need to get a nice hard drive icon, for my launcher link.
please note: Should I used directory instead of link (under TYPE)?
please note: My Second Drive, have one partition ext3 and NO SWAP,
is that OKAY?
and last: copying he the defaults in fstab file for the new drive /partition
is that okay as well?

--
If someone would take all these working procedures and make a STEP BY STEP,
that would HELP Thousands......

Cheers to All
:mrgreen:

---

### Post by zpro on 2006-05-26
One thing to ADD, 
make sure you chmod 777 the 80gb folder (oops) forgot that.
now it should allow you to create folders.

Rich

---

### Post by marken on 2006-05-31
[QUOTE=ifokkema]It gets worse - this won't work because Windows will not be able to read this drive. Fat32, according to microsoft, can't be bigger than 30 Gb or so. Windows will not be able to mount this drive.

Ivo[/QUOTE]

This is not true i think. Im no expert though. But currently i have a 150 Gb 32bit fat partition which windows XP finds just fine.

---

### Post by aysiu on 2006-05-31
For a long time I had a 100 GB FAT32 partition, and both Ubuntu and Windows was fine with it.

What I heard (and have yet to confirm myself) is that Windows cannot *create* a FAT32 partition larger than 30 GB.

---

### Post by ifokkema on 2006-05-31
[QUOTE=aysiu]For a long time I had a 100 GB FAT32 partition, and both Ubuntu and Windows was fine with it.

What I heard (and have yet to confirm myself) is that Windows cannot *create* a FAT32 partition larger than 30 GB.[/QUOTE]

Ah, yeah, sorry for not confirming that before I wrote it. Microsoft says the partition of FAT32 can reach up to 8 terabyte, but Windows (at least 2000) refuses to format (thus create) partitions larger than 32 Gigs. Not sure if WindowsXP can handle them, though.

Source: [http://support.microsoft.com/kb/184006/](http://support.microsoft.com/kb/184006/)

I have lots of problems with my Windows 2000 and my FAT32 share partition, and this problem was one problem I encountered. Currently, Windows messes up my ext3 partition where Linux is on, if I try to format my FAT32 partition. Really annoying, 'cause I just can't have both systems using it properly. Anyway, I opened a thread about that some time ago, but I got no reply.

---

