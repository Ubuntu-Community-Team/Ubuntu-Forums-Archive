---
title: "Full hard drive freakout freeze."
date: 2006-09-28
forum: Desktop Environments
---

### Post by mtaggart on 2006-09-28
Hello All,

I've been running Dapper Drake (exclusively, no other OS) on my 15" Mac PowerBook PPC for about six months, and had been LOVING it!  Until...

...today, when in the middle of checking my e-mail on Evolution, an alert popped up saying something to the effect of "Media Full: Contact Your System Administrator." I couldn't do anything-- quit the program, launch new programs, delete/move files, open the Terminal... ANYTHING.  So I restarted it, figuring if the disk was indeed full, I'd delete some files, in safe mode if needed.  

It now will give me the Ubuntu login screen, but any attempt to log in fails-- it just returns me back to the start.  I tried booting off the CD, using "rescue" as the parameter (I found that tip on another forum), and it claimed to not know what the heck I was talking about.

Why no warning, just the freeze-out?  Is my data gone?  I did a full backup recently, but I still have a few days' worth of work on there, not to mention the headache of facing a full re-install (I left Windows because of problems like that)-- it would be wonderful if anyone can tell me how I can crack into the disk again.

Many thanks in advance for your help!

---

### Post by genesis[OFT] on 2006-09-28
I very much doubt any data is lost.

Just boot up the Ubuntu install CD, choose the first option at the bootscreen ("Start or Install Ubuntu Linux" i think it is) and then, when you're at the desktop, mount your linux partition:

#>sudo mount -t ext3 /dev/hda1 /mnt/hda1

assuming that the partition that your data is on is formatted with 'ext3', it's on Primary (Master) IDE channel and that the mountpoint /mnt/hda1 exists.

Once it's mounted, go to the directory, and pick out what you need to delete, copy, edit, etc. and then reboot.

---

### Post by mtaggart on 2006-09-29
genesis,

Thanks for the quick response!

Booting from the cd, I didn't see "start or install," so I tried these options (using the "powerpc" option for each):

* live (default)-- Got me to a desktop, so I opened a terminal and typed the command you suggested.  It returned:

mount: mount point /mnt/hda1 does not exist

* rescue -- At the bootscreen, it returned:

cd:2,/install/powerpc/vmlinux : unknown or corrupt filesystem

Am I following your directions correctly?  If so, how do I confirm/check/change the parameters you described regarding the format (ext3) and mount point (/mnt/hda1)?

Again, many thanks-- I very much appreciate your time and assistance.

---

### Post by johnbl on 2006-09-29
[http://ubunt](http://ubunt)> uforums.org/showthread.php?t=257597

Had the same problem - a few times - try this.

---

### Post by qntgeek on 2006-09-29
> **mtaggart said:**
> genesis,
* live (default)-- Got me to a desktop, so I opened a terminal and typed the command you suggested.  It returned:

mount: mount point /mnt/hda1 does not exist


sudo mkdir /mnt/hda1

or change the directory /mnt/hda1 to a directory name that does exist

---

### Post by genesis[OFT] on 2006-09-30
Yep.

>sudo mkdir /<mountpointname>

and then put that in:

>sudo mount -t <filesystem> /dev/<hddname> /<foldername>

where

<filesystem> usually = ext3
<hddname> usually = hda1, hda2, hda3
<foldername> = /anything

:D

---

