---
title: "How do I resize Ubuntu partition? Linux dual-boot, not Windows"
date: 2006-01-02
forum: Desktop Environments
---

### Post by thumbsoup on 2006-01-02
When I installed Ubuntu 5.10 I let it install as essentially one primary partition taking the entire hard drive.  I now want to install Kanotix Linux on a smaller partitionm.  My problem seems to be that I cannot shrink the existing Ubuntu hda1 partition to create room for a new Kanotix partition.  BTW,  I do not have Windows installed, this is not an NTFS or FAT question.

Kanotix is based on Knoppix and comes with QTParted.  Booting from the Kanotix Live CD, I can use QTParted to see my drive partitions.

hda1  - Ubuntu primary partiation, ext3
hda2 - extended 
hda5 - swap (under hda2, and same size as hda2)

However, when I select the hda1 partition, the resize button is greyed out.   The hda1 partition is not mounted, but is Active.  When I right-click in QTParted and make it not active, the resize button is still greyed out.

Anyone know how I can resize my hda1 partition?

Thanks!

---

### Post by Sef on 2006-01-02
Have you tried partitioning with the Ubuntu 5.10 Live CD?   If that works then you know the problem lies with the Kanotix CD.

---

### Post by thumbsoup on 2006-01-02
Good idea, I will try that and report back.

---

### Post by thumbsoup on 2006-01-02
Nope, GParted from Ubuntu Live CD did not work.

I downloaded Ubuntu Live 5.10 and burned to CD.  The Live boot went fine, and I ran GParted.  GParted showed the same hda1, hda2/hda5 partition structure as stated in my first post.  GParted allowed me to choose to resize hda1 primary partition.  So far, so good.

I tried to shrink hda1 down to 50 GB (still 50% free space), and create 2 new primary partitions, each with about 30 GB.  

GParted then tried to create the new primary partitions, hda3 and hda4.

After about 15 minutes, I got an error message that GParted could not create hda3.   Then a couple minutes later I got the same message about hda4.

I cancelled the operation.  GParted then showed this partition structure:

/dev/hda1   ext3   

/dev/hda2   extended

/dev/hda5   linux-swap

/dev/hda3   unknown, 0 size

/dev/hda4   unknown, 0 size

Using the "delete" button in GParted I tried to delete hda3 and hda4.  This was apparantly successful, but when I rebooted back into my hard disk install of Ubuntu 5.10 (hda1) and ran GParted again, I still see these zero-size hda3 and hda4 partitions.

I am feeling lucky that I didn't destroy my main Ubuntu install on hda1, but I still want to repartition this drive!

Anyone have any ideas on how to do this?

Thanks.

---

### Post by plors on 2006-01-02
sounds interessting...
you could try the [gparted livecd]("http://gparted.sourceforge.net/livecd.php"). It contains one of the latest CVS versions of gparted and libparted and might be able to help you.

good luck!

---

### Post by thumbsoup on 2006-01-02
Thanks, I booted into GParted Live alpha3.  Seems to accept my resizing hda1, and creating 2 new partitions.  However, so far the "progress" window just has that horizontal bouncing bar, looks like Pong.  Been running for about 20 minutes, no apparent progress.  This is what happened when I ran GParted from the Ubuntu Live CD, before it produced the error message.

How long should it take to resize (shrink) a 110 GB partition down to 50 GB?

I am wondering if the length of time without apparent progress is itself a strong indication that the partitioning operation has failed, even without an error message.

---

### Post by plors on 2006-01-02
[QUOTE=thumbsoup]
How long should it take to resize (shrink) a 110 GB partition down to 50 GB?
[/QUOTE]

depending on the filesystem and the amount of used space a LONG LONG time. 
Shrinking a filesystem by 60GB could easily take hours, so don't worry too much yet :)

---

### Post by beameup on 2006-01-02
I'm having the same issue here trying to dual boot ubuntu/Kubuntu. The drive is listed as being busy. That's the problem. Was looking for an answer when I saw this thread. If I don't see a solution, I'll try resizing the swap partition and if that works, try making a new partition from that.

Just found this bit of advice which is probably the same for any partition manager:

> If QTParted whines about your disk device being busy, make sure you aren't swapping on the disk. If Knoppix detects a Linux swap partition it will automatically start to use it. Check with:

# swapon -s

Shut it off with:

# swapoff /dev/whatever

---

### Post by thumbsoup on 2006-01-02
Okay, taking the advice above about the resizing maybe taking a few hours, and some advice I got on the Kanotix forum about deleting the swap partition,  this time when booting with the GParted Live CD I did the following:

1) delete the hda2 extended partition and the hda5 linux swap (logical partition, the only thing in hda2). Refreshed GParted to make sure this was complete.

2) resized the hda1 partition to around 50 GB down from 110 GB.  This took, I think, around an hour.  I was out shopping (multi-tasking).

3) When I got back, GParted reported a resized hda1, and the rest of the drive as unallocated space.

4) created new partitions, in the order below, then applied all changes at once.  
- hda2 as primary partition in reiserfs at 30 GB
- hda3 as primary partition in ext3 at 30 GB
- hda4 as extended partition at 4.4 GB
- hda5 as logical partition under hda4, for linux swap, taking entire 4.4 GB

Gparted did all that in a few minutes.  This was all free space to begin with, I assume that is why it was so quick.

Rebooted into my original Ubuntu install on hda1, so far it works!

Thanks for all the help.  I will try to install Kanotix into the new hda2 partition next.

---

### Post by ShirishAg75 on 2006-01-03
Interesting, just posting here so I can come back & look later for this Gparted Live CD thread. thanx all.

---

### Post by alamba on 2006-01-03
I had the same problem using a ubuntu 5.10 live CD. Now I could try the method listed above but would rather not delete my swap partition. Is'nt there a way to resize / partition without deleting swap?

Akshay

---

### Post by beameup on 2006-01-03
Well, I ended up screwing up the partition somehow using the system rescue cd and qtparted, so I wiped the slate clean and resized it. Now dual booting Kubuntu/Ubuntu.

---

