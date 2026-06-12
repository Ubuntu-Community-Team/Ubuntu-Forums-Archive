---
title: "latest version of ntfs-3g"
date: 2009-01-31
forum: General Help
---

### Post by Teufel on 2009-01-31
Hello,

I have trouble using ntfs-3g for my external USB hard drive.
I have speeds of 3-4MB/s. Both my laptop and my hard drive are pretty new.
After googleing that issue, I found out that my version is very old:
```
ntfs-3g 1.2506 external FUSE 27 - Third Generation NTFS Driver

```

I then downloaded the lastest version from their page and tried to compile/install it:

[http://nopaste.voric.de/paste.php?f=upaopr](http://nopaste.voric.de/paste.php?f=upaopr)

I don't know how to fix that error.
Any ideas?

---

### Post by Gizenshya on 2009-01-31
NTFS-3g, to the best of my knowledge, is current.  Its what I use and I have no problems on any of my drives.

At first glance, it seems like it might be a USB version issue, rather than a file system/driver issue.

Are you sure your USB drive (device) AND your computer are both USB 2.0 compatible?  If not, it reverts back to USB 1.0, which is about the speed you were getting.

USB 1.0 is also known as "Full Speed," and USB 2.0 is also known as "Hi Speed."

---

### Post by Teufel on 2009-02-01
I bought both my computer and my USB Drive about a month ago. Both unused and new.
The weird thing is that for some reason I got 17MB/s yesterday.

No matter how fast the copying process is, my IO/Wait load is really high.
Also, how can ntfs-3g be the current release if it's 1.2.* and there is a 1.5.* out?

---

### Post by beyboo on 2009-02-01
As a part of trouble shooting did you try making the fs as fat32 to clearly isolate the problem to the ntfs-3g driver as you suspect ?

Linux is known to copy to USB2 devices at speeds which are half the speed at which you can copy off them. google on that and you will find out.

==> [http://www.google.co.in/search?hl=en&q=linux+usb+copy+slow&btnG=Google+Search&meta](http://www.google.co.in/search?hl=en&q=linux+usb+copy+slow&btnG=Google+Search&meta)

---

### Post by Teufel on 2009-02-01
I have a lot of data on the USB drive, and afaik I can't convert the drive without risk of data loss.

---

### Post by Teufel on 2009-02-05
Any other ideas, anyone?

---

### Post by Teufel on 2009-02-22
I push this topic again, still looking for a solution.
I now managed to install the Stable Source Release 2009.2.1 from [www.ntfs-3g.org](www.ntfs-3g.org), but a minute later, the old version popped up in my update manager. I did test it, it didn't make any difference whatsoever. I still get speeds of about 3-4MB/s, and while copying, I can not use my computer at all. It completely freezes, sometimes not even the cursor will move.

I'm really desperate about this, I wish someone knew how to fix this.
Thanks.

---

### Post by szaka on 2009-02-26
> **Teufel said:**
> I bought both my computer and my USB Drive about a month ago. Both unused and new.
The weird thing is that for some reason I got 17MB/s yesterday.
No matter how fast the copying process is, my IO/Wait load is really high.

The speed fluctuation and the very high IO/Wait clearly shows an USB/hardware problems, totally unrelated to the NTFS-3G file system driver. Try these:
[http://ntfs-3g.org/support.html#slow](http://ntfs-3g.org/support.html#slow)
[http://ntfs-3g.org/support.html#ioerror](http://ntfs-3g.org/support.html#ioerror)

---

### Post by Teufel on 2009-03-09
> **szaka said:**
> The speed fluctuation and the very high IO/Wait clearly shows an USB/hardware problems, totally unrelated to the NTFS-3G file system driver. Try these:
[http://ntfs-3g.org/support.html#slow](http://ntfs-3g.org/support.html#slow)
[http://ntfs-3g.org/support.html#ioerror](http://ntfs-3g.org/support.html#ioerror)


I now defragmented the drive (which took 4 days straight), but the speed has not improved.
I'm trying to rule out all the listed causes for my problem:

    *  Not using at least NTFS-3G version 1.5012.

I'm not, but I tested the latest version and it didn't work (that's what the thread is about)

    * Writing multi-GB files on a highly internally fragmented volume.

I defragmented the volume entirely, using Windows on VirtualBox.

    * Some software are using the most inefficient block sizes by default.

Does that mean copying software? I tried rsync, cp and gvfs-copy and they're all about the same speed, although rsync doesn't eat all my cpu power.

    * A highly sparse file is being regularly written or updated.

Don't really know what that means, but I don't write or update anything on there regularly.

    * Some software indeed do intensive file operations sometimes (Beagle, Amarok collectionscanner, updatedb, Spotlight, etc).

I have that drive in my amarok collection, but even if amarok isn't running it's just as slow.

    * The CPU usage is not directly visible in case of kernel file system drivers but this is not true for user space drivers. That is, they are in the process list unlike the kernel drivers. Higher CPU usage is normal and expected in some scenarios. This is true for most file systems, not only NTFS-3G.

Again, not sure what this means. I'm using kernel 2.6.27-9-generic

    * The NTFS block size (cluster size) is smaller than 4096 bytes. This often happens, for instance, if FAT32 was converted to NTFS. The driver always logs this information for block devices. You can search for the value of the 'blksize' in the system log files under the /var/logs directory. Typically this information can be found in the 'messages' or 'daemon.log' log file, depending on your operating system.

**This might be it:** I did buy the drive formatted as FAT32, then reformatted it to NTFS and then deleted everything on it. But the log file says otherwise:

```
dom@r61:/var/log$ cat daemon.log | grep blksize
Mar  7 01:38:09 r61 ntfs-3g[10752]: Mount options: rw,nosuid,nodev,uhelper=hal,silent,allow_other,nonempty,relatime,fsname=/dev/sdb1,blkdev,blksize=4096 

```

    * Using an embedded device or a very fast I/O subsystem (100+ MB/s, RAID).
I'm quite sure that has nothing to do with my hardware setup, does it?

    * VMware is not using "mainMem.useNamedFile=FALSE" in the .vmx file. 
I'm not using VMWare.


Unfortunately, the IOerror site doesn't help me, since I don't get any IOErrors, but a high IO/Wait.

Thank you so much for your help, I really appreciate it.

---

### Post by Teufel on 2009-03-19
I now also defragged the drive using my VirtualBox Windows, which took about three days.
Still the same problems.
The funny thing is, that the speed varies - sometimes it goes up to 20 MB/s and then slows down, sometimes I even get 40MB/s, if transferring small files, like 100MB or so.

But usually it's a HD movie I move, about 5GB in size. Then it's mostly speeds of 4-6MB/s.

---

