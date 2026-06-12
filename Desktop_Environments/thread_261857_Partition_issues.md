---
title: "Partition issues"
date: 2006-09-20
forum: Desktop Environments
---

### Post by seismicmike on 2006-09-20
I know this is technically in the wrong place b/c I have Breezy instead of Dapper, but it's a general Linux issue anyway, so suck it up and deal :razz:.

I have a dual boot on a 40gig hard drive ( :sad: ) ... I have 10gig set apart for Windows, 5gig for Ubuntu and the rest on a 3rd ext3 partition that I mount in both (so I can access files in both without having to use a thumb drive, which seems idiotic to me, and without having to mount the Windows or Linux system partition)...

all was well... until recently. I don't know what I did or why this happens, but it used to be that every 30 mounts (which was actually quite frequently) the hda3 (ext3) partition (which will hereby be referenced as my E drive b/c that's what it is in Windows and it's flat out easier to say) had to be checked, which would take about 60-120 extra seconds in the boot sequence, would work fine and then I'd get on with my life, but a few weeks ago it suddenly started coming up at that point and saying that the E drive contains errors and thus checking it every time. Not only that, but the check it performs fails somehow and it goes into fsck (which looks really vulgar if you just glance at it, as was pointed out to my Windows-lubber colleague), which subsequently fails and the boot sequence stops alltogether and I have to press [CTRL] + D to get it to go on. It goes on as if everything is normal and the comptuer works fine. So my questions are:

1. Does anybody have any idea what this error might be?
2. Does anybody have any idea how I can fix it?
3. When I first set up my system like this, the default it gave me for my mount point for the E-drive in Linux was /home/, to which I saw no objection so I accepted it. Could this somehow be the problem? If so is there anyway (without a complete redo) of fixing it?
4. Why does Linux make such a big deal out of this if it doesn't even seem to affect anything **except** the boot sequence?

Thank you very much for your help.

---

### Post by seismicmike on 2006-09-20
I think I may have fixed this.

Here's what happened:

```
* Checking all file systems...
/home contains a file system with errors, check forced.
/home:
Inode 277695 has illegal block(s)

/home: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY
   (i.e., without -a or -p options)

                                       [fail]

* fsck failed. Please repair manually.
* CONTROL-D will exit from this shell and continue system startup

root@(none):~# _
```

Until today I had just been typing [CTRL] + D and going on with startup, but today I typed "fsck" and got:

```
fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
/dev/hda3 is mounted

WARNING!!! Running e2fsck on a mounted filesystem may cause SEVERE filesystem damage.

Do you really want to continue (y/n)? _
```

Not wanting to destroy my partition, I typed "n", but I guess it decided to continue anyway b/c:

```
check aborted
e2fsck 1.38(30-Jun-2005)
/home contains a filesystem with errors, check forced
Pass 1: Checking inodes, blocks and sizes.
```

at this point there was a long pause followed by about ten minutes of "Such and such block has such and such error, fix?" to which I replied no for a while, but then started replying yes. After a while it had me delete some files that wer apparently messed up (I only deleted ones I didn't care that much about) and then it cleared these blocks. Then I ran fsck again and it cleared everything up and then I rebooted and it worked fine.

Hope this helps anyone else who has the same problem. I just wish I knew what caused this in the first place so I can avoid it next time.

---

