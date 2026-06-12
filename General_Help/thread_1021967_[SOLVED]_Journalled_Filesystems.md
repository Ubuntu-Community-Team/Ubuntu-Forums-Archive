---
title: "[SOLVED] Journalled Filesystems"
date: 2008-12-26
forum: General Help
---

### Post by Goll on 2008-12-26
I've been doing a lot of research on different filesystems.
So far, I've come to conclusion that "big files" are used very well in xfs filesystems.
In this case, I was going to split things up a lot-
I'm not sure about the whole Reiserfs deal, (I don't think I'm going to do it, it's too risky.)
I'm finding it's not something I would want to do, unless it was Reiser4.

From what I've read, **jfs** has minor problems in "every day situations" (Whatever that means.)
And I've read...  a lot of benchmarks.

I know that ext4 has come out, but I've never compiled a kernel before,
So I'm assuming I'll have that the next Ubuntu release. (Or until I learn how to do it.)

I'm just trying to get a perspective here, on **what qualifies for "big files" and, if it's worth it to separate my files for using an XFS filesystem.**

I have a lossless music collection in FLAC, and I'm dealing with 4gb-8gb files occasionally (Probably 2 times a week.)

But then I have pictures; I have, a torrentfile sandbox (if you will)-
that everything is centralized around (because I used to run windows with a dual boot, but **then realized I like separating the torrent files onto a separate harddrive anyway.)**

I'm all linux; x64. I'm planning on TrueCrypting this-

I want something stable for storage, but I want to split that from the torrent files and small things (system files), etc.
But I hear Reiserfs loses its "speed" after a month (idk, how can you trust forum posters.)

It's all very confusing. But I'm trying to figure it out. One forum thread/essay at a time.

I have an external **1TB**, which I immediately formatted to **ext3** (Finding 20gb resorted to "root files" (Is that what they're called?)

Then Reiser4 came to be around **25mb** or so.
(But still,

I'm not exactly looking for speed, I'm looking for stability.

Concerning XFS, yes I am aware that power failures = prob sudden Atomic explosion of the world which is my computer.

Yet, I consider... idk, all of my videos to be not accessed as much. (I suppose I would separate the seeding folder into something more small file friendly. But, I don't always download small files, so.

Maybe I could have separate directories for large downloads and small. 

The music that I am archiving in my computer is irreplaceable. Very important. No I am not seeding it; separate section.
Consider each to be around 50mb- But I am not sure the smallest file XFS would prove efficient for.
400mb?

Would a power outage cause files that aren't even being used to be damaged as well?
If so, I suppose I wouldn't mount **that** one @ boot.

idk, I like feedback. If someone has some experience with filesystems, I'd like the hear, I'm very interested in the topic.

---

### Post by northern lights on 2008-12-26
In short:

ext3 wastes a much larger portion of the maximum partition capacity than doe ReiserFS, XFS or JFS.

JFS and XFS are generally quicker to mount, unmount and create than are Reiser and ext3.

JFS and XFS also handle large files faster than Reiser and ext3. JFS requires the least CPU usage when copying/moving/deleting large files. Especially removal is much much faster on JFS and XFS.

Copying/moving large numbers of medium to small files are where ext3 comes out on top. XFS is close, ReiserFS and JFS are slower here. ext3 still sucks when it comes to deletion/removal.

For searching and listing, ReiserFS and XFS are considerably faster than the other two, but also more CPU intensive.

XFS appears the most suiting for a home or small business server.

There was a good essay on debian-administration.org, I'll post it, if I find it.

---

### Post by Goll on 2008-12-26
> **northern lights said:**
> In short:

ext3 wastes a much larger portion of the maximum partition capacity than doe ReiserFS, XFS or JFS.

JFS and XFS are generally quicker to mount, unmount and create than are Reiser and ext3.

JFS and XFS also handle large files faster than Reiser and ext3. JFS requires the least CPU usage when copying/moving/deleting large files. Especially removal is much much faster on JFS and XFS.

Copying/moving large numbers of medium to small files are where ext3 comes out on top. XFS is close, ReiserFS and JFS are slower here. ext3 still sucks when it comes to deletion/removal.

For searching and listing, ReiserFS and XFS are considerably faster than the other two, but also more CPU intensive.

XFS appears the most suiting for a home or small business server.

There was a good essay on debian-administration.org, I'll post it, if I find it.

I appreciate your input. Thank you.
I've been essentially testing out the effects of having different systems installed-since that appears to me to be the more effective way of finding out.
The external I had ended up being formatted as JFS (Maxtor by the way-which I hear is antilinux, but I fear that's just a little too conspiratorial for my taste)
The JFS wouldn't even mount after I reinstalled. (Giving a not-so-telling error message that was quite discouraging.)
Something to do with the superblock.

From what I've heard, ext3 makes many copies of the superblock. I haven't heard about JFS doing this; and if that were true, I suppose that would explain the overhead coming from ext3-(But I've heard the journalling is more effective using JFS.)
I find it ironic it screwed up on its second mount.

**(Update)**I found this: *"If this information lost, you are in trouble (data loss) so Linux maintains multiple redundant copies of the superblock in every file system.*" on [http://www.cyberciti.biz/tips/understanding-unixlinux-filesystem-superblock.html]("http://www.cyberciti.biz/tips/understanding-unixlinux-filesystem-superblock.html")

Reiser acted weird (not surprisingly) when I used it for the Ubuntu system.

In intentionally crashed it, to see how it acted. And I remembered someone saying that it *waits* for the cache to be written to disk (I have no idea what I'm talking about) before opening another process-be it vi...
leading to badly balanced process management.

---

### Post by 2hot6ft2 on 2008-12-26
> **northern lights said:**
> In short:

ext3 wastes a much larger portion of the maximum partition capacity than doe ReiserFS, XFS or JFS.

JFS and XFS are generally quicker to mount, unmount and create than are Reiser and ext3.

JFS and XFS also handle large files faster than Reiser and ext3. JFS requires the least CPU usage when copying/moving/deleting large files. Especially removal is much much faster on JFS and XFS.

Copying/moving large numbers of medium to small files are where ext3 comes out on top. XFS is close, ReiserFS and JFS are slower here. ext3 still sucks when it comes to deletion/removal.

For searching and listing, ReiserFS and XFS are considerably faster than the other two, but also more CPU intensive.

XFS appears the most suiting for a home or small business server.

There was a good essay on debian-administration.org, I'll post it, if I find it.
Very well put. Also for your consideration I submit the following.
> Ubuntu Linux as well as UUE, unless you have set it up otherwise, uses the EXT3 system by default.  There are 3 journaling methods for EXT3 system:

    * Journal Data Writeback
    * Journal Data Ordered
    * Journal Data

     By default "journal data ordered".  In data=ordered mode, ext3 only journals metadata, but it logically groups metadata and data blocks into a single unit called a transaction.  When it's time to write the new metadata out to disk, the associated data blocks are written first.  In general, data=ordered ext3 filesystems perform slightly slower than data=writeback filesystems, but significantly faster than their full data journaling counterparts.


Taken from here [http://ubuntusoftware.info/Howto_tweak_ubuntu_ultimate.html](http://ubuntusoftware.info/Howto_tweak_ubuntu_ultimate.html)
which also has tweaking the various file systems XFS included.

---

### Post by dcstar on 2008-12-27
> **Goll said:**
> ........
idk, I like feedback. If someone has some experience with filesystems, I'd like the hear, I'm very interested in the topic.

I use a Reiserfs partiton for my VMWare VMs, because they are essentially one large file that has many read/writes into it and it seems to perform better than using EXT3 with its many small file optimisation.

It's all about "horses for courses", you find the base application(s) that you are trying to use and then find the filesystem that works best (reliability, performance, resilience etc).

---

### Post by Goll on 2008-12-27
> **northern lights said:**
> In short:

ext3 wastes a much larger portion of the maximum partition capacity than doe ReiserFS, XFS or JFS.

JFS and XFS are generally quicker to mount, unmount and create than are Reiser and ext3.

JFS and XFS also handle large files faster than Reiser and ext3. JFS requires the least CPU usage when copying/moving/deleting large files. Especially removal is much much faster on JFS and XFS.

Copying/moving large numbers of medium to small files are where ext3 comes out on top. XFS is close, ReiserFS and JFS are slower here. ext3 still sucks when it comes to deletion/removal.

For searching and listing, ReiserFS and XFS are considerably faster than the other two, but also more CPU intensive.

XFS appears the most suiting for a home or small business server.

There was a good essay on debian-administration.org, I'll post it, if I find it.

Would you consider a standard 50mb FLAC file a big file?

---

### Post by snova on 2008-12-27
> **Goll said:**
> From what I've heard, ext3 makes many copies of the superblock. I haven't heard about JFS doing this; and if that were true, I suppose that would explain the overhead coming from ext3-(But I've heard the journalling is more effective using JFS.)
I find it ironic it screwed up on its second mount.

As I recall, the superblock is copied when fsck runs, which I think is done every boot (the more comprehensive checks are run every 20/30 mounts or so). So this doesn't affect the overhead at all.

---

### Post by northern lights on 2008-12-28
> **Goll said:**
> Would you consider a standard 50mb FLAC file a big file?
It's just terminology, after all, but I'd call it medium.

When I'm calling files small, I'm thinking of ogg/mp3s, textdocuments, spreadsheets and the like.

When I'm calling files large, I'm thinking of CD/DVD .isos, 700MB .avis and such.

Still, moving documents and music can easily result in operations on thousands of files. .flacs you'll probably operate on by the dozen. So in the context of file operations, I guess you could/should classify them as large.

[Promised debian-administration.org article]("http://www.debian-administration.org/articles/388")

---

### Post by Goll on 2008-12-28
I found this linked from somewhere:
[http://thebs413.blogspot.com/2005_08_01_thebs413_archive.html](http://thebs413.blogspot.com/2005_08_01_thebs413_archive.html)

I have found it to be **very** informational.

I'm not kidding, look at it. 

> **northern lights said:**
> 

[Promised debian-administration.org article]("http://www.debian-administration.org/articles/388")

I appreciate it.

Here; [http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)
They talk about enabling Barrier=1 for Ext3 filesystems, to do md5 checking.
I'm trying to figure out how to do that now.

---

