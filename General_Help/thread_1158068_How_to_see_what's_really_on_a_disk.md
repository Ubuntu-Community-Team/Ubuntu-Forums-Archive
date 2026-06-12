---
title: "How to see what's really on a disk?"
date: 2009-05-13
forum: General Help
---

### Post by craig100 on 2009-05-13
H,

I've just added a new hard drive to my Ubuntu 9.04 x64 installation. I've also made the new drive my home partition. However, as I had a couple of goes at copying the data over, I deleted the first attempt, or so I thought. I now see in the system monitor that the new drive has 128GB used, whereas my home directory is only 22GB. How can I see exactly what's on the new drive and delete what I don't want there.  The drive was formatted and partitioned originally so there shouldn't be anything left over from the original Windows partitions.

Thanks in advance

Craig

---

### Post by craig100 on 2009-05-13
Just a little further on, I installed and used TestDisk to see what was on the new drive. It showed quite a few big files marked as "Deleted". However, I can't see them from Nautilus as me or root so is there anyway of removing these files?

Craig

---

### Post by oldos2er on 2009-05-13
Empty the trash.

---

### Post by craig100 on 2009-05-13
Thank you.

Not as simple as that or I'd already have done it.  These are files on the new disk that TestDisk shows as marked for deletion, but don't appear in the trash can.  I can only see them using TestDisk and see the space they take up with GParted or System Monitor.

Craig

---

### Post by oldos2er on 2009-05-13
Sorry--it's not always easy to ascertain someone's experience level by their questions.

 What file system are you using on the drive?

---

### Post by raptor2552 on 2009-05-13
> The drive was formatted and partitioned originally so there shouldn't be anything left over from the original Windows partitions.
Have you deleted the windows file system?

---

### Post by craig100 on 2009-05-13
Yes the Windows file system is gone.  The drive has been totally repartitioned with GParted.  The files I copied over initially for my home partition didn't have the username directory so I deleted the files that had been copied and started again. I think it's these initial files that were just marked for deletion but not actually removed.  So instead of having a 22GB home directory I seem to have a 128GB home directory.  I can't see these files in Nautilus, not even started as root. I can only see them using TestDisk but that doesn't let me get rid of them.

---

### Post by stathol on 2009-05-13
I guess I'd start by trying to narrow it down with du.

Maybe something like:

```
du --max-depth=2 /home
```

That should give you at least a *broad* view of where the bulk of the files might be.

---

### Post by perrti-y02 on 2009-05-13
If you run the program "baobab" it will give you a nice picture. It achieves the same thing as the previous post but if you are a more visual person it might help you more. Baobab, I think, is installed by default.

---

### Post by craig100 on 2009-05-13
Thanks will run the baobab thing soon.  I'm just copying the the home directory from the new drive to a third drive to see if it copies the deleted files. If it doesn't then I'm out of the woods. I'll just set the 3rd drive as home and repartition the old home drive. Takes ages though.

I must say I'm getting pretty downhearted. I seem to spend 80% of my time messing around with machinery instead of working on developing web sites.  Wonder if I should just go back to Windows when Win7 comes out.  Ubuntu is still to "toy town" for everyday use I sometimes feel though it's getting better with each release.

---

### Post by stathol on 2009-05-13
Well, I'll be darned. Applications -> Accessories -> Disk Usage Analyzer (a.k.a. baobab)

I was just wondering if there was something equivalent to WinDirStat for Linux, and well, there you go.

---

### Post by craig100 on 2009-05-15
Used the Disk Usage Analyser as you suggested and it showed me exactly what files had sneaked onto the disk during a failed /Home transfer. What a great tool! So was able to remove them and gain 67GB of space with the help of this post too: [http://ubuntuforums.org/showthread.php?t=157434](http://ubuntuforums.org/showthread.php?t=157434).

So no re-install required, excellent result, thanks:)

---

