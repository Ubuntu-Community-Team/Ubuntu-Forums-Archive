---
title: "No permissions on mounted ext3 drive"
date: 2005-11-29
forum: Desktop Environments
---

### Post by MDoten on 2005-11-29
Hi,

I recently formatted an NTFS drive and changed it to ext3. I edited /etc/fstab so that it would be automatically mounted. The line looks like so:

/dev/hdb1       /media/stuff    ext3    defaults        0       0

When the hard drive gets mounted, it's only root that has access to it. I have tried many random things, hoping that it would magically work, all to no avail. How should I have the line in fstab so that it will work? Or is that even the problem? Could it be a problem with the way the folder was created before the mounting has even begun?

Thanks in advance,

~Mark

---

### Post by aysiu on 2005-11-29
Did you know *defaults* means only root can read it?
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by MDoten on 2005-11-29
Ok, so by fixing that, and adding rw (so that I can write to it as well), it still doesn't seem to work. The line that I have now is:

/dev/hdb1       /media/stuff    ext3    rw,user 0       0

After changing it, I unmounted it, and typed *sudo mount -a* (which is supposed to remount /etc/fstab). When I type *ls -l* in the /media folder, the line for the hard drive looks like this:

drwxr-xr-x  3 root root 4096 2005-11-29 11:23 stuff

---

### Post by MDoten on 2005-11-30
Hey,

I figured out the problem. As root I changed the owner of the folder where I was mounting to. After doing this, I gave myself write access, and bingo, it works :D 

Thanks for all the help

~Mark

---

### Post by Limulus on 2005-12-01
I have an external USB hard drive that was formatted as "vfat" and so wouldn't allow files larger than 4 GB (this was a problem because I wanted to use [Simple Backup]("http://sourceforge.net/projects/sbackup/") to backup more than 4 GB of data and it puts it all in a single file ^^; ) so I formatted it as ext3 and then had the same problem you did.

Ubuntu would mount it as /media/usbdisk so based on what you said, I tried changing the permissions on it, but every time it unmounted, Ubuntu deleted the directory.  This was just a little annoying ;)  The fix is to create /media/usbdisk and change its permissions (I used *sudo nautilus*) when the disk wasn't mounted.

---

### Post by Chippendale on 2005-12-03
i have a question

```
/dev/hda4       /media/hda4     ext3    user,rw,auto    0       2
```

what do the numbers mean  "0"   "2"  i know you can change them to 1 also but i dont know what they mean

---

### Post by flopsy on 2005-12-03
Leave them at 0 2.

From man fstab:

       The  fifth  field,  (fs_freq),  is  used  for  these filesystems by the
       dump(8) command to determine which filesystems need to be  dumped.   If
       the  fifth  field  is not present, a value of zero is returned and dump
       will assume that the filesystem does not need to be dumped.

       The sixth field, (fs_passno), is used by the fsck(8) program to  deter&#8208;
       mine the order in which filesystem checks are done at reboot time.  The
       root filesystem should be specified with a fs_passno of  1,  and  other
       filesystems  should  have a fs_passno of 2.  Filesystems within a drive
       will be checked sequentially, but filesystems on different drives  will
       be  checked  at  the  same time to utilize parallelism available in the
       hardware.  If the sixth field is not present or zero, a value  of  zero
       is  returned  and fsck will assume that the filesystem does not need to
       be checked.

---

