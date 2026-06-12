---
title: "disappearing drive"
date: 2009-03-13
forum: General Help
---

### Post by petemga on 2009-03-13
I just intsalled ununtu for the first time and installed it on a different disk than my C: drive containing windows XP. Once I installed ubuntu, I got it all set up and then booted back into windows and could no longer see that drive in the "my computer" menu. How do I get it so I can see the drive in windows and ubuntu? I have read around but am new to this so please excuse me. I am guessing that it is a partition issue. 

Thanks.

---

### Post by taurus on 2009-03-13
Normally, windows don't detect ext2/ext3 filesystem.  If you want to access your Ubuntu partition(s) in windows, you need to use fs-driver, [http://www.fs-driver.org/](http://www.fs-driver.org/).

And if you want to access windows while you are in Ubuntu, install ntfs-config use it to configure your ntfs partition.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

---

### Post by LittleCory on 2009-03-13
Do you mean you installed ubuntu on a different physical drive, or just on a new partition within the free space on your windows drive?  At any rate, windows can't read the file system you are using for ubuntu, probably ext3.  That is why you cannot see it.  I don't know if there is support for ext3 available at all for windows, I don't believe there is though.

You could always create a different partition within the ubuntu partition that could be read by windows, that is make it NTFS.  Basically I think you would create a new partition within the ubuntu partition, and format it NTFS, and then mount it whereever you wanted in order to store your data.  Just leave the ubuntu partition, the one that contains the os, with a few gigs of extra space so that you can add components to it.

---

### Post by petemga on 2009-03-13
cool, thanks! I thought I had created the addtional partitions on the new drive and left the rest of the drive alone, which was already formatted as NTFS. Oh well, I will format the rest of the drive so that XP will recognize it and leave the ubuntu partions alone. That is what I figured had happened, i just thought that when I created the partitions for Ubuntu I had done it correctly but apparently not. :-k

---

### Post by petemga on 2009-03-13
i am trying to install gparted through a terminal with the command sudo apt-get install gparted and when it asks me for my password it wont let me type anything. numbers, letters, nothing. whats up with that?

---

### Post by taurus on 2009-03-13
It won't show up on the screen as you type it so just type in your password and hit the Return key.

---

### Post by petemga on 2009-03-14
oooh duh! thanks!!


BTW-> Im in Deland, FL. nice to see a fellow Floridian. :D

---

### Post by horax on 2009-03-14
I am having a very similar issue.

I have three drives.  On drive 1 I have my XP OS.  On drive 2 I have my Ubuntu OS.  Drive 3 is strictly for storage/backup issues.

Installation went smoothly with me choosing Disk 2 for Ubuntu, NTFS.  Initially I could see ALL drives both in XP and in Ubuntu.

Now I cannot see Drive 2 from EITHER XP or Ubuntu.  Ironically, I can see Drives 1 and 3 in BOTH OS's.
I really would LOVE to see Drive 2 as I am trying to keep all applications, files, and anything else Linux-y on that drive for performance tests and the like.

Any ideas on how to get around this?  It's really bothering me!

horax


:popcorn:

---

### Post by taurus on 2009-03-14
> **horax said:**
> I am having a very similar issue.

I have three drives.  On drive 1 I have my XP OS.  On drive 2 I have my Ubuntu OS.  Drive 3 is strictly for storage/backup issues.

_Installation went smoothly with me choosing Disk 2 for Ubuntu, NTFS_.  Initially I could see ALL drives both in XP and in Ubuntu.

Now I cannot see Drive 2 from EITHER XP or Ubuntu.  Ironically, I can see Drives 1 and 3 in BOTH OS's.
I really would LOVE to see Drive 2 as I am trying to keep all applications, files, and anything else Linux-y on that drive for performance tests and the like.

Any ideas on how to get around this?  It's really bothering me!

horax

:popcorn:

You have windows on first drive (or first partition); you installed Ubuntu on second drive (or second partition) with ntfs filesystem?

---

### Post by horax on 2009-03-14
Yes.

Weird thing is that even though LInux is on Drive 2, you cannot 'see' Drive 2 from within Linux.

I could understand not seeing it in Windows, but why wouldn't it see itself?

hx

---

### Post by taurus on 2009-03-14
> **horax said:**
> Yes.

Weird thing is that even though LInux is on Drive 2, you cannot 'see' Drive 2 from within Linux.

I could understand not seeing it in Windows, but why wouldn't it see itself?

hx

Looks like you have created a new thread.

[http://ubuntuforums.org/showthread.php?t=1095917](http://ubuntuforums.org/showthread.php?t=1095917)

---

### Post by horax on 2009-03-14
> **taurus said:**
> Looks like you have create a new thread.

[http://ubuntuforums.org/showthread.php?t=1095917](http://ubuntuforums.org/showthread.php?t=1095917)

Yes, but for a separate question initially...the main reason of the other thread is for the choosing of the OS discrepancy, not for the disappearing HD.  I just added that info as I was not sure if was relevant or not.

---

### Post by jelle_ on 2009-03-14
in fact everything you open in ubuntu is at disk 2, except disk 1 and 3. to show this you can open your file manager and click the computer button at the top. you will see an disk called filesystem. this is disk 2.

---

### Post by horax on 2009-03-14
Oh...so can I rename FileSystem to anything I want so I can recognize it as my second HD?

I guess this really isnt' any kind of issue, then?
I was envisioning FileSystem as "My Computer" from windows, wherein you can choose your HD, etc.

hx

---

### Post by jelle_ on 2009-03-14
i'm affraid i haven't got that working. the problem is that ubuntu uses the drive all the time, so you cannot unmount it, which is needed for gparted. 

i always access it by typing /

---

