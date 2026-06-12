---
title: "mkfs.ext3:"
date: 2006-03-17
forum: Desktop Environments
---

### Post by jwe on 2006-03-17
Hi

I am getting this error when I try and create a new logical volume.
mkfs.ext3: Permission denied while trying to determine filesystem size

Does anyone have any info on this?

Thanks.

---

### Post by rattking on 2006-03-17
Hello
Just to be sure are you running mkfs.ext3 with sudo?

---

### Post by jwe on 2006-03-17
Hi

Yes I am.

---

### Post by jwe on 2006-03-17
nope sorry I was not.
That would be it ):  Thanks!

---

### Post by dmber on 2007-09-03
i am getting this error:

/dev/hdb is entire device, not just one partition!
Proceed anyway? (y,n) y
/dev/hdb is apparently in use by the system; will not make a filesystem here!

when i try to use this command.  i am trying to make a mount point for my hard drive.  when i tried to create the mount point, it told me the hdd needed a filesystem, which got me here.

help?
thanks!

---

### Post by merlinus on 2007-09-03
Ubuntu mounts hdd partitions, not drives.  You can use gparted to make these, either the one on the live cd or gparted live cd from [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

It will allow you to split the hdd into partitions and format them.  Then you can mount them in ubuntu.

gparted live cd will bypass mounted disks, which you cannot partition nor format.

-merlin

---

### Post by dmber on 2007-09-03
thank you.  that did it.  i got no error when mounting the partition in the terminal.  new problem: i can't find the drive (partition) anywhere.  where do i go to find it?  when it was unmounted i could see the drive in Places/Computer.  But it's not there anymore.  I see my floppy drive, my dvd drive, and a hard drive called "file system" (the smaller hdd that ubuntu was installed on) but no "storage" drive.

thank you very much.



EDIT: nevermind.  i found it.  i went to Places/Computer/File System/Media/Storage and it says there are 111GB free space.  


YES!!!

---

### Post by dmber on 2007-09-03
ok, one more problem.  i tried to created a folder in the Storage folder and it said i do not have permission to write to this folder.  how can i change that?

thank you!

---

### Post by merlinus on 2007-09-03
Try this:

```

sudo chmod -R 775 /media/Storage

```

assuming it is formatted as ext3 or other linux fs.

-merlin

---

### Post by dmber on 2007-09-03
i got it!

i had to put my username where 775 is, but it worked!  

thank you so much for your help merlin.  i even edited the fstab to get it to automount on startup.  i'm so excited.  thank you for your help!

---

### Post by merlinus on 2007-09-03
You are most welcome.  Glad it is working!

-merlin

---

