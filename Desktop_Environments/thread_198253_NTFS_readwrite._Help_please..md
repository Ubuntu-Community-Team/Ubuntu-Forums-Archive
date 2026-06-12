---
title: "NTFS read/write. Help please."
date: 2006-06-16
forum: Desktop Environments
---

### Post by kpkeerthi on 2006-06-16
Guys,
I have a huge collection of music and pictures (on a logical NTFS partition) that I have been using on my WinXP. Now that I'm dual booting dapper with windows, it would be great if I could mount the partition in dapper. At the moment I can read the files without a hitch from dapper. It would be nice if I can also write to it.

1. Has anyone tried enabling read/write on a NTFS volume from dapper? 
2. What kind of problems have you encountered? 
3. Which is the recommended and the most stable package that I should use? 
4. Should it fail, will I loose only data or my entire hard disk be hosed (buy a new one)? 
5. Any other gotchas that I should be aware of. 

Thanks.

---

### Post by x64Jimbo on 2006-06-16
NTFS writing support is very sketchy. There was a project a while back called CaptiveNTFS but it has been abandoned for a while. The best thing for you to do is create a "share" partition that is fat32 formatted. Both Linux and Windows can read and write to fat32 partitions.

---

### Post by reidi on 2006-06-16
Hmmm... My Dapper desktop has folder icons for my other partitions.  I just double-click to access files.  I play music from my "XP" partition all the time, using my Linux players.

In fact when I look at /etc/fstab I can see that the partitions are getting mounted at boot.  You can also see this if you just type "mount" at a terminal prompt.

I'm not up on the latest NTFS info, but it used to be a BAD idea to try and write to an NTFS partition.

---

### Post by beameup on 2006-06-17
FYI: The next version of Xandros which is to be released this month (Xandros 4) is advertising NTFS write. Your going to pay for it of course, but not as much as you'd pay for Windows.

[I]"And Much More...

NTFS
Now you can read and write to a Windows NTFS partition."[/I]

[http://www.xandros.com](http://www.xandros.com)  Click on the preorder window.

You can make a new partition and format it FAT32 and both OS'es will write to it. Best thing to do is make your Ubuntu partition bigger and move everything there!

---

### Post by garethppls on 2006-06-17
Just on terms of NTFS reading. When I click on my NTFS partition it says "I dont have the permissions neccessary to view it" can anyone help. This partition is 200GB so its important to be able to read from it at least

---

### Post by woot on 2006-06-17
[QUOTE=garethppls]Just on terms of NTFS reading. When I click on my NTFS partition it says "I dont have the permissions neccessary to view it" can anyone help. This partition is 200GB so its important to be able to read from it at least[/QUOTE]

can you copy paste the contents of the fstab file?
(supposing your on gnome, else gedit should be kate i think
```
gedit /etc/fstab
```

---

### Post by zorglab on 2006-06-17
[QUOTE=x64Jimbo]NTFS writing support is very sketchy. There was a project a while back called CaptiveNTFS but it has been abandoned for a while. The best thing for you to do is create a "share" partition that is fat32 formatted. Both Linux and Windows can read and write to fat32 partitions.[/QUOTE]

I've tried CaptiveNTFS a while ago, it's incredibly slow and unstable. A no go.
NTFS write support included in the kernel is useless, you can only edit existing files without changing their size.

As for a shared partition, fat32 is rather dumb fs. The thing that bothers me most is that you can't have files larger than 4GB.
A better solution, is to set up an ext2 or ext3 partition and install the Ext2 IFS driver in Windows ([http://fs-driver.org/](http://fs-driver.org/)). The only drawback is that this driver doesn't support utf8 and thus, some caracters may appear weird under windows.

---

### Post by garethppls on 2006-06-17
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

funny this because the hdd on NTFS is called /dev/sda1 in the computer view

---

### Post by stoneguy on 2006-06-17
[QUOTE=beameup]FYI: The next version of Xandros which is to be released this month (Xandros 4) is advertising NTFS write. [/QUOTE]

Unless the folks at Xandros have pushed into the lead on this capability, the more accurate description would be NTFS write **much of the time**. But of course, marketeers are loathe to qualify their statements.

The reality is that, yes, you can overwrite information in a file on an NTFS drive. But if its size changes, well, maybe you can and maybe you can't. Same goes I believe for allocating new files. 

KNOPPIX 5 is the current FOSS leader in this technology. It's gotten to the point where the subsystem will gracefully refuse to try to alter the partition instead of trashing it. Eventually some band of whiz kids will finish reverse engineering the NTFS control structures and get it all done right.

---

### Post by helpdeskdan on 2006-06-17
I got it working in knoppix once just to access some files.  However, as others have stated, I would use fat32 if possible.  Consider yourself warned.  The following instructions at the forum would probably work for ubuntu.  
[http://www.knoppix.net/forum/viewtopic.php?p=94929](http://www.knoppix.net/forum/viewtopic.php?p=94929)
more info:
[http://www.linux-ntfs.org/](http://www.linux-ntfs.org/)

I don't use captive-ntfs anymore; it was a pain to get working & buggy.  If development weren't halted, perhaps it would work by now.  A shame.

---

### Post by beameup on 2006-06-22
[QUOTE=stoneguy]Unless the folks at Xandros have pushed into the lead on this capability, the more accurate description would be NTFS write **much of the time**. But of course, marketeers are loathe to qualify their statements.

The reality is that, yes, you can overwrite information in a file on an NTFS drive. But if its size changes, well, maybe you can and maybe you can't. Same goes I believe for allocating new files. 

KNOPPIX 5 is the current FOSS leader in this technology. It's gotten to the point where the subsystem will gracefully refuse to try to alter the partition instead of trashing it. Eventually some band of whiz kids will finish reverse engineering the NTFS control structures and get it all done right.[/QUOTE]

[http://www.xandros.com/news/press/release66.html](http://www.xandros.com/news/press/release66.html)

It's Paragon software

"Xandros and Paragon Software Shatter Last File Barrier within a Multi-platform Framework
Paragon Universal File System Technology Empowers Xandros Desktop Users to Save Music, Photos, and Documents to Windows Machines

NEW YORK, NY and Buggingen, Germany —Xandros, the leading provider of easy-to-use Linux alternatives to Windows desktop and server products, and Paragon Software Group, the leading provider of innovative software solutions in storage management and data safety, today announced that Paragon's “NTFS for Linux” is shipping with the upcoming Xandros desktop release. The technology shatters the last barrier to transparent file sharing within a multi-platform framework. Xandros users will now be able to edit and save their music, photos and documents to shared folders on any Windows or Mac PC."

It'll be 3 or 4 months before they release the OCE (free) version.

---

### Post by Kouya on 2006-06-22
[QUOTE=garethppls]Just on terms of NTFS reading. When I click on my NTFS partition it says "I dont have the permissions neccessary to view it" can anyone help. This partition is 200GB so its important to be able to read from it at least[/QUOTE]

follow this guide:

[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)

had no problems with it. Was able to mount 4 NTFS drives (each in separate folder of cos) on every boot to read them.

---

