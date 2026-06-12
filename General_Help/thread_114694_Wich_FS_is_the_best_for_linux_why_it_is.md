---
title: "Wich FS is the best for linux? why it is?"
date: 2006-01-09
forum: General Help
---

### Post by maduranga on 2006-01-09
hello... :) 

 i'm new to linux. i have seen that most linux distros use ext3 fs. but some peoples say that the best FS for linux is a file system named ReiserFS of something like that... anyway, what do u think? wich FS is the best? why do u think that it is the best?

   post ur idea and let us know.............

---

### Post by handy on 2006-01-09
Great question, I've been wondering the same thing.

Thanks for asking it!

handy

---

### Post by johna11en on 2006-01-09
ReiserFS is supposed to be a faster file system.  I recently switched to it from Ext3.  I haven't noticed a big difference.  I am using a Pentium 4 notebook with 1 gig of ram.

Ext3 has been around for a lot longer and seems to be the default option for most distributions.

---

### Post by byen on 2006-01-09
[QUOTE=johna11en]ReiserFS is supposed to be a faster file system.  I recently switched to it from Ext3.  I haven't noticed a big difference.  I am using a Pentium 4 notebook with 1 gig of ram.

Ext3 has been around for a lot longer and seems to be the default option for most distributions.[/QUOTE]

Ah. beat me to it.. yes..though people say ReiserFS is still not totally stable...many use it without much trouble. Ext3 is right now (and has been)  the standard FS used while using Linux. 
Personally I use Ext3 (tried and tested to work OK!)
Goodluck.

---

### Post by lgmdaniel on 2006-01-09
How easy is it to switch over? Is it just a simple conversion, or will I have to create a new partition and move everything over?

---

### Post by Bender NZ on 2006-01-09
If you want to change to reiserfs you will have to reformat the entire partition, you can't just convert it.

---

### Post by lgmdaniel on 2006-01-09
I take it then this is something I could do before I install Ubuntu then? If so what tools will I need to boot and configure the partitions?
Will the swap need to be touched?
And will Ubunta happliy install on this new partition?

---

### Post by johna11en on 2006-01-09
[QUOTE=lgmdaniel]I take it then this is something I could do before I install Ubuntu then? If so what tools will I need to boot and configure the partitions?
Will the swap need to be touched?
And will Ubunta happliy install on this new partition?[/QUOTE]

During the Ubuntu installation process you have the option of manually creating the partitions.  When you use this option you can select ReiserFS. When I installed it I didnt change the swap.  In my case Ubuntu is working fine under ReiserFS.  I did not experienced any problems or have to do anything special.

---

### Post by WakkiTabakki on 2006-01-09
[QUOTE=johna11en]ReiserFS is supposed to be a faster file system.  I recently switched to it from Ext3.  I haven't noticed a big difference.  I am using a Pentium 4 notebook with 1 gig of ram.

Ext3 has been around for a lot longer and seems to be the default option for most distributions.[/QUOTE]

Check this one out!
[http://linuxgazette.net/122/TWDT.html#piszcz](http://linuxgazette.net/122/TWDT.html#piszcz)

And, well, "better" when it comes to file systems has (IMHO) more to do with stability than raw speed...

/N

---

### Post by DaMasta on 2006-01-09
I've used ext3 and xfs. I can't say I could tell a difference.

---

### Post by slux on 2006-01-09
It's a good but also a hard question.

While the above article indicates good performance for ext3 (slightly behind JFS overall), I've seen ones where the rest totally annihilate it and that one was criticized for having such a low performance processor on the machine. Apparently at least ReiserFS is intentionally using more CPU than ext3 in order to be more smart about I/O and the CPU may have become the bottleneck in those tests.

You'll easily find some more benchmarks with conflicting results if you google a bit and Namesys, the company that created ReiserFS, has some as well.

Stability probably isn't an issue unless you choose Reiser4 as all the major competitors have had ample time to mature. I've used and continue to use Reiser3, XFS, JFS and ext3 and while there have been a couple of incidents of filesystem corruption during the past 8 years, I can't say that I've found any one of them more robust than another.

The differences probably won't be large enough for people to notice them during daily use since the workloads vary so greatly and we're talking about a few seconds here and there if all implementations are reasonably good.

Of all the options, ReiserFS is special in that Hans Reiser and his team have some fresh ideas for improving filesystems and their work is really state of the art - you won't find a similar implementation in other operating systems.

XFS is by Silicon Graphics and especially good at handling huge files I hear. JFS comes originally from AIX and seems to boast good performance with a very long history albeit not such a long one with Linux itself (if the stability is your thing). 

ext3 is ext2 with journaling added. Often thought to not be so fast but very reliable. The LinuxGazette article shows that in some setups it can be quite fast too.

---

### Post by lgmdaniel on 2006-01-09
I come from a AIX background and JFS is very reliable, even after system crashes and other problems. The only time I've ever seen any major problems it was due to disk crashes or bad applications. Though there is a JFS2 which has even more flexiblity and gets around the 1TB filesystem limits (yes I've hit those a few times). Having not played with Linux that much I didn't realise all these extra formats where also avalible, so thanks for the enlightenment.
Thats the problem with teaching yourself on the fly, there are lots you miss. :smile:

---

### Post by Azriphale on 2006-01-09
In my everyday, desktop use of ext3 and ReiserFS (which is Reiser v3), I have seen no big differences between the two. 

I was running ReiserFS with SuSE because it is the default there, and now I am using ext3 in Ubuntu because that is the default there. Except for a while, my home drive was still ReiserFS, but I have recently switched completely over to ext3 so that everything is uniform.

On a home desktop machine, I don't think it would make much difference either way. Only, I would say that you should not attempt Reiser4, as it is still not entirely stable in the 2.6.x kernel. From what I have read, it is supposedly a whole lot faster than ext3 and ReiserFS (v3) in a lot of tasks, but also a bit slower in others, but I don't remember the details.

ext3 has had time to mature, and is a stable, robust fs.

The only corruption problems I have had are on NTFS :smile: 
Still got to try to recover my data....
I keep just about everything on ext3 on my PC, and I have another still running SuSE 9.3, which uses ReiserFS.

Hmm.. While I'm here, just a passing thought - Anybody know some software to recover NTFS data from a missing/completely screwed partition? Preferebly Free Open Source Software.

---

### Post by gingermark on 2006-01-09
I believe that there is a Windows driver for ext2 available, and that one for ext3 also exists. I don't know if there are drivers for other Linux file systems available, but for new Linux users who are likely to be dual-booting surely this could be one criteria for a file system to be judged on?

---

### Post by rejser on 2006-01-09
I thought that reiserfs is more optimized to handle larger files, while ext3, is an older version which has better handling for smaller files.
Storage for movies in reíserfs and system on ext3?
I run ext3 on all.

---

### Post by handy on 2006-01-09
There is something out there that lets you see ext3, atleast from windoze.

No names sorry.

handy

---

### Post by Thirsteh on 2006-01-09
[QUOTE=maduranga]hello... :) 

 i'm new to linux. i have seen that most linux distros use ext3 fs. but some peoples say that the best FS for linux is a file system named ReiserFS of something like that... anyway, what do u think? wich FS is the best? why do u think that it is the best?

   post ur idea and let us know...........[/QUOTE]

ext3 is the best for a "normal" desktop user with both small and large files, while ReiserFS is ABSOLUTELY brilliant if you have an insane amount of small files and directories, unfortunately however, it's not as good as ext3 when it comes to very large files.

---

### Post by rejser on 2006-01-09
ext2explorer, also works with ext3

---

### Post by rejser on 2006-01-09
[QUOTE=Thirsteh]ext3 is the best for a "normal" desktop user with both small and large files, while ReiserFS is ABSOLUTELY brilliant if you have an insane amount of small files and directories, unfortunately however, it's not as good as ext3 when it comes to very large files.[/QUOTE]

isn't it the other way around?

---

### Post by Suger on 2006-01-09
[http://www.fs-driver.org/](http://www.fs-driver.org/) is an ext2/ext3 driver for Windows. As for other dual booters, be aware that there is no support for reiserfs in OpenBSD, and I'm not sure there is in FreeBSD or even in NetBSD (but that remains to be checked).

---

### Post by Azriphale on 2006-01-09
Suger, you beat me to it.

the driver from [www.fs-driver.org](www.fs-driver.org) allows you to mount ext2/ext3 partitions in windows with read and write permissions. I am using it, and it is pretty good. Only it doesn't mount one of my drives. Small problem, its the "/" drive, and I mostly need the others, so it doesn't bother me. This tool assigns each drive a windows drive letter. 

To pull stuff off my ReiserFS drives, when I still used ReiserFS, I used a combination of rfstool and a GUI for it called YAReG. Go to 
[http://yareg.akucom.de/](http://yareg.akucom.de/)
to get them. Its not as convenient as the ext2/ext3 driver, which assigns each drive a windows drive letter.

I don't know about ReiserFS support in NetBSD or FreeBSD. And I need to finish downloading OpenBSD so I can try it out.. Can't wait for that.

---

### Post by bannerboy on 2006-01-09
I personally use ext3, I've had to cold reboot my computer for several reasons lately, and I've never lost any data.

---

### Post by handy on 2006-01-10
Who needs to access Ubuntu from windoze anyway?  It sure is easy to loose track.

handy

---

