---
title: "fsck-ing wiped out my data"
date: 2009-06-23
forum: General Help
---

### Post by alecmunro on 2009-06-23
Hi All,

I'm running kubuntu 9.04, and very much enjoying it.

I had the need to resize an ext3 partition on an external drive yesterday, so I installed the "partition manager" software from the repository.

I started the software, specified the resizing, and let it do it's business.

When I returned, it had stopped, because there were errors checking the drive. I was able to save most of the log that it generated, but it is too large (250KB) for me to attach to this post.

Anyway, when I mounted the drive afterwards, it appears to be missing a folder containing about 200GB of data. Some of this includes our family photos from the last 3 years, of which I have only partial backups. As such, solving this is essential to me remaining alive, and my wife remaining out of prison. (I am mostly joking).

"lost+found" on this drive now contains a huge number of entries.

Here's a massively condensed version of the log:

```

Shrink partition ‘/dev/sdb1’ from 420.01 GiB to 318.43 GiB 
Job: Check file system on partition ‘/dev/sdb1’ 
Command: e2fsck -f -y -v /dev/sdb1 
e2fsck 1.41.4 (27-Jan-2009)
Pass 1: Checking inodes, blocks, and sizes
Error reading block 7471106 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

```
... happens about 40 times
```

Error reading block 100827138...

Pass 2: Checking directory structure
Entry 'media' in / (2) has deleted/unused inode 35618817.  Clear? yes

Entry '..' in ??? (35619235) has deleted/unused inode 35618835.  Clear? yes

```
... Happens about 200 times, mostly on '..', but sometimes on specific files, and there are a few of the following messages:
```

Entry '..' in Error reading block 28770306 (Attempt to read block from filesystem resulted in short read).  Ignore error? yes

Force rewrite? yes

```
... Then we get to:
```

Pass 3: Checking directory connectivity
Unconnected directory inode 35979288 (...)
Connect to /lost+found? yes

```
... Happens several hundred times, then
```

Pass 4: Checking reference counts
Inode 2 ref count is 11, should be 10.  Fix? yes

Inode 3623025 ref count is 4, should be 3.  Fix? yes

```
... This continues for several thousand lines, with a couple of other messages thrown in:
```

Unattached inode 36372551
Connect to /lost+found? yes

Inode 14139434 (...) has invalid mode (00).
Clear? yes

```
... Twice, the following message appears (the filesystem was not mounted, as far as I could tell).
```

WARNING: PROGRAMMING BUG IN E2FSCK!
	OR SOME BONEHEAD (YOU) IS CHECKING A MOUNTED (LIVE) FILESYSTEM.
inode_link_info[14139438] is 3, inode.i_links_count is 1.  They should be the same!

```
... Then we get to:
```

Pass 5: Checking group summary information
Block bitmap differences:  -(7054135-- ....Lots of stuff....)
Fix? yes

Free blocks count wrong for group #215 (65535, counted=11687).
Fix? yes


```

That's what I've got. Help is very much appreciated.

---

### Post by HermanAB on 2009-06-23
Hmm, it is time to buy a bullet proof vest and a backup disk drive...

You have to copy the disk using dd, then work on the copy.

---

### Post by bodhi.zazen on 2009-06-23
First you need to stop using the disk.

Next you can look at something like photorec, it is in the ubuntu repositories (install testdisk).

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

It is a good idea to work from an image as suggested by HermanAB.

---

### Post by alecmunro on 2009-06-23
Well, the backup drive I think I can manage.

Once I have the data copied, what can I do with it? Most of the solutions I have found mostly seem to deal with recovering individual deleted files. That is certainly much better than not recovering them, but it would be preferable to restore the entire directory structure, which is something I have been unable to find any information.

Thanks.

---

### Post by alecmunro on 2009-06-24
Ok, so I have a new hard drive, and I am using dd to copy the old partition. It's been running about 16 hours so far, and is less than half done. There have been several thousand read errors so far, which makes me concerned that there is a physical problem with the old drive.

---

### Post by alecmunro on 2009-07-02
Well, photorec found a whole bunch of things, but very little of what I was looking for. However, I was able to find practically everything in lost+found, so I'm a relatively happy camper.

---

### Post by hangfire on 2009-07-02
> **alecmunro said:**
> Well, photorec found a whole bunch of things, but very little of what I was looking for. However, I was able to find practically everything in lost+found, so I'm a relatively happy camper.

So please change the title of the thread... fsck'ing rarely if ever destroys data. It only makes the extent of the destruction known.

-HF

---

### Post by alecmunro on 2009-07-03
> **hangfire said:**
> So please change the title of the thread... fsck'ing rarely if ever destroys data. It only makes the extent of the destruction known.

-HF

I think removing a 300GB+ directory and relegating it's contents to assorted folders under lost+found is severe enough that I will keep the title, thanks. At least until I have recovered 100% of my data, then perhaps I will change it to "hid my data".

---

