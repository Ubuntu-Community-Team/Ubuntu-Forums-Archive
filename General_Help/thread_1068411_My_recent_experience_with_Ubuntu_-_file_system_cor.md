---
title: "My recent experience with Ubuntu - file system corruption"
date: 2009-02-12
forum: General Help
---

### Post by Triptoph on 2009-02-12
Installed Ubuntu-eee 8.04 on my Asus eee 1000H a couple months ago.  One physical drive with a small windows NTFS partition that was not used with the Ubuntu installation, a small Ext3 partition dedicated to Ubuntu, and a large Ext2 partition mounted at /home.  The idea was, if i messed up the config or whatever with Ubuntu, I could reinstall on the small Ubuntu Ext3 partition, and keep the Ext2 partition with all my data untouched.

Had a few instances where I had to reboot, and the last time this happened, when I restarted, during the file system check it reported that there was some problem with the file system and asked me to repair it manually (!) Ha!  Well, anyways I ran fcsk and it reported that because the drive was currently mounted it was unsafe to use it, so i told it no, not to do it.  

And it continued on its way to ask then if i wanted to repair various errors it had found.  I assume it had skipped the mounted partition and was now processing another one -- sound right?  

After I asked it to repair the problems it found, I rebooted and it reported that it could not open my home folder anymore, and there were serious screen redraw issues - pieces of windows would show up when i moused over them, then disappear later.

From my limited knowledge, I suspect that the Ext3 partition was skipped while running the disk check, but it attempted to fix errors on the large Ext2 partition mounted at /home, and didn't fix them so well, so /home became unusable.  

I need a reliable, stable system.  I am now considering something I never thought i would -- switching to MacOS X as it promises a more reliable and stable environment to work under (PHP dev work).  I wonder though, would it have helped if I had the large partition as Ext3 with its journaling support?  I thought the only advantage though was that you don't have to wait for it to go through a lot of data upon startup after a bad shutdown?  Surely Ubuntu cannot be as unstable as this incident seems to show?  

Your thoughts on this are appreciated.

---

### Post by jrusso2 on 2009-02-12
This was why I was so glad when Linux got journaling file system.  Reiser.  Ext 2 always corrupted if it lost power, or if you locked up and had to shut down.

Luckily now there is some better journaling file systems and most of them work pretty well except I don't like ext 3 cause of the disk check and it still can corrupt.

---

### Post by mb_webguy on 2009-02-12
Just out of curiosity, why did you use ext2 for your /home partition instead of ext3 (which supports journaling)?

---

### Post by Triptoph on 2009-02-12
> **mb_webguy said:**
> Just out of curiosity, why did you use ext2 for your /home partition instead of ext3 (which supports journaling)?
I had used fs-driver with windows previously in an attempt to have the larger partition accessible from both winXP and Ubuntu using Ext3.  It says it is compatible with both, but was built for Ext2 but it didn't work for me and clicking on the drive in windows gave me a prompt asking me if I wanted to format it.  I tried Ext2 this time hoping it would be more compatible and actually work this time (never used WinXP so never tried it!)

---

### Post by 1ronlung on 2009-02-12
Since installing Kubuntu a couple of months ago, on two occassions I've had to reach for Super Grub Disk 'cos the mbr or grub got corrupted.. Generally when running windoze apps through Wine..

I'm sticking with it though.. Nothing so far that wasn't easily repairable :)

---

### Post by Triptoph on 2009-02-12
> **1ronlung said:**
> Generally when running windoze apps through Wine

One of the times I had to hard-reboot was related to running a windows app through wine as well.  


I wonder what file system the Mac uses... hmm.

MBR corruption... i've never run into that on any variant of windows since XP came out except when related to hard drive death.  Maybe Ubuntu based on Ext2/3 really IS that fragile??  Must be someone out there who will say this isn't so...?

---

### Post by jrusso2 on 2009-02-12
> **Triptoph said:**
> One of the times I had to hard-reboot was related to running a windows app through wine as well.  


I wonder what file system the Mac uses... hmm.

MBR corruption... i've never run into that on any variant of windows since XP came out except when related to hard drive death.  Maybe Ubuntu based on Ext2/3 really IS that fragile??  Must be someone out there who will say this isn't so...?

Plenty will say that but everyone has their own opinion but mine comes with 13 years of Linux experience.

---

### Post by mb_webguy on 2009-02-12
> **Triptoph said:**
> I had used fs-driver with windows previously in an attempt to have the larger partition accessible from both winXP and Ubuntu using Ext3.  It says it is compatible with both, but was built for Ext2 but it didn't work for me and clicking on the drive in windows gave me a prompt asking me if I wanted to format it.  I tried Ext2 this time hoping it would be more compatible and actually work this time (never used WinXP so never tried it!)

Ahh...  I see your problem.

If you're dual-booting and want to have a separate /home directory and a partition to share data between the two OSes, then you should have a separate /home directory AND a partition for shared data, and they shouldn't be the same partition.  Your shared data partition can be ntfs if you want to ensure compatibility with Windows, and Ubuntu handles ntfs well.  

Your /home partition should be separate from this so you don't expose your Linux configuration files to Windows, and create the potential for accidentally breaking your Linux account from Windows.  Your home partition can be formatted as ext3, which makes it more crash-resistant since ext3 supports journaling.  Since you're keeping your data somewhere else, your /home partition doesn't need to be large, since configuration files are text files and therefore fairly small.  About 2GB should be sufficient (though if you use Wine, you should either move the .wine directory to the shared partition or increase the size of your /home directory a bit).

---

### Post by Triptoph on 2009-02-12
> **mb_webguy said:**
> Ahh...  I see your problem.

If you're dual-booting and want to have a separate /home directory and a partition to share data between the two OSes, then you should have a separate /home directory AND a partition for shared data

Thank you, that is an excellent suggestion.  Although it doesn't really touch on the file system being fragile.  Is Ext2 really much more fragile than Ext3?

---

### Post by jrusso2 on 2009-02-12
Keep using ext2 and you will find out for sure.

---

### Post by MarblePanther on 2009-02-12
Hehe, hold down the power button and then watch your boot up screen:)
error error error bad sectors....

---

### Post by mb_webguy on 2009-02-12
> **Triptoph said:**
> Thank you, that is an excellent suggestion.  Although it doesn't really touch on the file system being fragile.  Is Ext2 really much more fragile than Ext3?

Journaling significantly decreases the chance of corruption in the event of a system crash or power outage.  So in that sense, yes -- ext2 is "more fragile" than ext3, since the primary difference between the two is that ext3 is a journaling filesystem.  It's the same reason why the Windows world doesn't use FAT32 for internal partitions anymore (and only uses FAT32 for maximum portability for external storage).

---

### Post by Triptoph on 2009-02-13
I wonder how Ext3 compares with HFS+, Mac OS's file system in terms of reliability and coping with hard crashes.  Anyone have any experience there?

---

### Post by Yashiro on 2009-02-13
You crash often enough for this to be a real issue?

---

### Post by Triptoph on 2009-02-13
> **Yashiro said:**
> You crash often enough for this to be a real issue?

If a system is capable of crashing, and it seems all of them are, of course this is a real issue.

---

### Post by jdong on 2009-02-13
Using ext2 does put you at risk of irreparable  corruption after a bad shutdown, and using third party proprietary ext2 drivers certainly does the same.

At any rate, I've always said that fsck is **NOT** a tool you go around playing with -- it isn't some magical disk wizard that waves a wand over your drive and fixes things. Before going down the fsck path always:

(1) Ask people you consider experts for their opinion
(2) Mount the drive read-only and pull as much info as possible
(3) If (2) not possible, then make a binary backup image of the drive.


In my experience, and this goes for EXT2/3, reiserfs, XFS, NTFS, and FAT32, it's not at all abnormal for the fsck tool in cases of bad corruption to cause a bigger mess than the one you started with!


Another thing -- **fsck tools are not things to guess with** -- every assumption you make could be at the cost of valuable data. Anytime  you're not 100% sure what you are doing with a filesystem repair tool, stop, read the documentation or ask someone for help!

---

### Post by Triptoph on 2009-02-13
Thanks jdong.

After backing up your data, are there any better options than running fsck to attempt a repair?

---

### Post by Yashiro on 2009-02-13
Well some people crash once a year. Your post makes it seem like you experience this once a day!

HFS+ in my experience is no better or worse than Ext3.
However, I don't crash more than a few times a year on my Mac and PC's combined, so my basis for comparison is not that great.

I'd probably stick with Linux for data simply because you have a greater chance of someone knowing what to do when it breaks. Such technical knowledge from Mac forums is few and far between.

---

### Post by jdong on 2009-02-13
> **Triptoph said:**
> Thanks jdong.

After backing up your data, are there any better options than running fsck to attempt a repair?

Easy methods? No, running a fsck in a "fsck -fy" manner is probably the only feasible repair method for the average user. Usually if you manage to get all the data off, the motivation for doing this is to make the system bootable again without resorting to a reinstall, and this can be a hit-or-miss.

The other case where you want to repair the filesystem is if the damage is bad enough that you can't get all of your data out. If that's the case, ext3 experts (deities) do have magical tools like debuge2fs that can interact with the filesystem at a low level and recover more data through human intervention than an automated tool can. But that's not something that I know how to do :)

The use of fsck can be such a crapshoot with severe data corruption, which is why I stress the importance of doing as thorough of a backup as possible before playing around.


Again, my sympathies for going through filesystem corruption incidents like this -- I've been through (and been called to fix) many cases like this on virtually every platform and filesystem, and the pain is universal. Although tempting, don't take away from this experience that filesystem Y is less likely to corrupt than filesystem X because person Z said they've been using it for 20 years without problems...

The only recommendation I'll make is avoid using non-journaled filesystems such as FAT32 and EXT2. Apart from that, most journaled filesystems available will provide you a comparable level of resistence against nasty filesystem corruption like this, but still be aware that doesn't translate to "pull the plug at will with no consequences" (figuratively; not saying that you would do that!)

---

### Post by Triptoph on 2009-02-13
> **Yashiro said:**
> Well some people crash once a year. Your post makes it seem like you experience this once a day!

I'd probably stick with Linux for data simply because you have a greater chance of someone knowing what to do when it breaks. Such technical knowledge from Mac forums is few and far between.

On the other hand, when you do find it it's likely that their suggestions are going to be exactly right for your setup, simply because your setup is exactly the same as everyone else's a lot of the time :)

I didn't have a crash on linux for a couple months, then 3 in a week -- but then I was using it 16-17 hours every day for the entire week and I really stressed it with a lot of apps running simultaneously.  My Vista box which is much more well-used has crashed hard twice in the few years i've had it.

---

### Post by Triptoph on 2009-02-13
> **jdong said:**
> The only recommendation I'll make is avoid using non-journaled filesystems such as FAT32 and EXT2. 

That's probably the single most important piece of information I'm taking home from this whole thread I think -- that I really should have used Ext3 instead of 2 for both partitions in question.  I have reinstalled Ubuntu-eee with this config... Although I mounted it as /home again (did this before making this thread... next time i'll mount the large partition at /data or something like that)

---

### Post by jdong on 2009-02-13
Maybe I should share some info on my experience:

I've got my laptop where I play with the latest bleeding-edge everything on it, and kernel panics, hardlocks, or my simple stupidity destabilizing the system is not at all abnormal. I've been through every filesystem deemed reliable (ext3, JFS) or designed uncorruptible (reiser4) and they've all managed to screw themselves up to the point that it's not possible to repair.

I have a separate system with a large XFS storage array attached which I use to store all my valuable files. I might mirror parts of it on my other computers for convenient local access but at the end of the day it all goes back onto that server. It's kept up on a very very conservative setup (Hardy + hardy-updates, no external repos) and rarely if ever goes down unexpectedly (last time it went down I dropped a bunch of textbooks on the external disks... OOPS).

This might be something to consider if you are a tinkerer by nature, like me.

---

### Post by Triptoph on 2009-02-13
Funny you should mention that.  I have recently been toying with the idea of getting another system as a file server among other server tasks.  Right now all my data is kept on a separate NTFS drive under Vista, with a program called Second Copy 7 copying all changes from this one data drive to an identical second drive to cover the case when one dies, but it would be better backing up to a separate system altogether.

---

