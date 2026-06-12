---
title: "do we have a partition editor that can...?"
date: 2006-11-01
forum: Desktop Environments
---

### Post by mdurham on 2006-11-01
Do we have a partition editor for Gnome that can grow a partition downwards?
I've tried gparted but it apparently can only grow upwards (to the right). I wonder why it can't grow downwards?
Cheers, Mike

---

### Post by ReaderRat on 2006-11-01
I don't know of one. Here is the place for the most recent partitioner:[**Gnome PARTition EDitor = gparted**](http://gparted.sourceforge.net/index.php).  I believe it has something to do with the MBR (Master Boot Record).

---

### Post by bettlebrox on 2006-11-01
>I've tried gparted but it apparently can only grow upwards (to the right). I wonder why it can't grow downwards?

Maybe because the parition is fragmented and there is data at the end of the drive, resizing would delete or overwrite the data?

---

### Post by mdurham on 2006-11-01
> Maybe because the parition is fragmented and there is data at the end of the drive, resizing would delete or overwrite the data?
bettlebrox, that may be the case but I can do it with partition magic under Windows. I really should be able to do it from Linux somehow.

---

### Post by CatKiller on 2006-11-02
GParted can. It didn't used to be able to move the start of some partition types, but the latest version can.

Don't forget to run from a live cd environment, and to back up any important data before you start.

---

### Post by mdurham on 2006-11-02
CatKiller, I wanted to grow the start of an unmounted ext3 partition that had 10Gb empty space in front of it (lower, on the left). There was no way that I could see how to do this as the partition representation in the editor occupied the whole rectangle. In other words there was no space to drag the partition to the left.
If you know of a way to do this can you let me know.
Thanks, Mike

---

### Post by CatKiller on 2006-11-02
If the partition you're trying to move/resize is a logical drive in an Extended partition, then you need to make the Extended partition bigger first. You can't make something larger than the box it's in.

If I've misinterpreted what you've said, then you'll have to explain your symptoms again :)

---

### Post by mdurham on 2006-11-02
CatKiller, maybe I didn't make it clear, sorry about that.
I want to grow (to the left) "/dev/hda6" see attached pic.

---

### Post by CatKiller on 2006-11-02
You're trying to resize a mounted partition. You **really** don't want to do that. That's what all the padlocks are for.

Boot from the [GParted live cd]("http://gparted.sourceforge.net/livecd.php"), and then try the operation again.

EDIT: Actually, it doesn't look like that's your root partition, which is the normal problem with trying to do this in your normal Linux environment, so you **should** be OK if you just unmount that partition before fiddling with it. **sudo umount /media/hda6** should do it. Although you'll probably still want to use the GParted cd because of its newer version that can move the start of an ext3 partition.

---

### Post by FastZ on 2006-11-02
I just wanna chime in here because I am trying to do the same thing on my machine.  The 10Gb Linux partition I set up a long time ago is at the end of the hard drive and I have a 27Gb gap between the ext3 formatted partition and the NTFS partition at the start of the hard drive.  I want to fill that gap with the ext3 partition and end up with an almost 40Gb ext3 partition for Linux.  I dont really have a need for multiple partitions under Linux but if I have to do it that way, then I guess I wouldn't have a problem with it.  I have a lot of stuff that I want to keep on my Linux partition now and if I resize it, will my Ubuntu install be screwed up?

---

### Post by mdurham on 2006-11-02
CatKiller, I *DO* understand about unmounting first, the screenshot was onlu for the purpose of explaining the problem as you didn't understand my previous post. When I try to do the resize of course I unmount it first. It's just that there appears no way of resizing to the left. If you do know a way please tell me.

My advice to FastZ is, do it in Windows.

Thanks

---

### Post by CatKiller on 2006-11-03
> **FastZ said:**
> I just wanna chime in here because I am trying to do the same thing on my machine.  The 10Gb Linux partition I set up a long time ago is at the end of the hard drive and I have a 27Gb gap between the ext3 formatted partition and the NTFS partition at the start of the hard drive.  I want to fill that gap with the ext3 partition and end up with an almost 40Gb ext3 partition for Linux.  I dont really have a need for multiple partitions under Linux but if I have to do it that way, then I guess I wouldn't have a problem with it.  I have a lot of stuff that I want to keep on my Linux partition now and if I resize it, will my Ubuntu install be screwed up?

Make a backup of the important stuff before you start. A crash at the wrong time, or the wrong click of the mouse, and it could all be gone. Aside from that, it's fairly safe.

The procedure should be very straightforward for you - download the GParted cd. Boot from it. Resize the partition. Restart.

Good luck.

---

### Post by CatKiller on 2006-11-03
> **mdurham said:**
> It's just that there appears no way of resizing to the left. If you do know a way please tell me.

Which version of GParted are you using?

---

### Post by FastZ on 2006-11-03
Thanks.  I'll try to take care of that this evening after work.  Hopefully all goes well.

EDIT:  I just logged into Windows and using Paragon Partition Manager, I resized my 10gb Linux partition to take over the empty, unformatted space before it (27gb approx.).  The resize went smoothly without error, I booted into Ubuntu just fine after a disk check said that it found errors and fixed them.  But now, my Desklet that monitors hard drive space still says that I only have 10gb of space on this partition.  How do I find out if the 27gb I just added is actually usable?

---

### Post by mdurham on 2006-11-03
> **CatKiller said:**
> Which version of GParted are you using?

I'm using Ver: 0.2.5

---

### Post by CatKiller on 2006-11-03
> **mdurham said:**
> I'm using Ver: 0.2.5

You should download the newer one then. I believe, although I haven't checked the changelogs, that full move support came in 0.3.

---

### Post by mdurham on 2006-11-03
> **CatKiller said:**
> You should download the newer one then. I believe, although I haven't checked the changelogs, that full move support came in 0.3.

Thanks for that CatKiller. I'm using the latest from Edgy's repos, I thought that would be up to date. I'll have a look at their (gparted's) web site.
Cheers, Mike

---

