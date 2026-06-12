---
title: "ext3 filesystem corrupt. How can I recover my files?"
date: 2009-06-17
forum: General Help
---

### Post by kung fu buntu on 2009-06-17
I got home from work and while using the computer I tried to copy one file from one HDD to another, but cp returned an error telling me the system is read only.

I try to ls the mountpoint contents as root and I get a "total 0".
But by typing "ls /mntpoint/some_dir" I can navigate through the subdirectories and access files.

Advised by some people I force a fsck and reboot the system.

This is the log file:
> Log of fsck -C -R -A -a -f
Wed Jun 17 20:16:33 2009

fsck 1.41.0 (10-Jul-2008)
/dev/sdc1: Superblock has an invalid ext3 journal (inode 8).
CLEARED.
*** ext3 journal has been deleted - filesystem is now ext2 only ***

/dev/sdc1: Resize inode not valid.

/dev/sdc1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
        (i.e., without -a or -p options)
/dev/sdb1: 66960/78464 files (24.4% non-contiguous), 59582858/80325000 blocks
/dev/sdb2: 11/40800 files (0.0% non-contiguous), 50657/41766991 blocks
fsck died with exit status 4

Wed Jun 17 20:25:26 2009
----------------



When I try to run e2fs, I get:
> #e2fsck  /dev/sdc1
e2fsck 1.41.3 (12-Oct-2008)
Resize inode not valid.  Recreate<y>?
Isn't this destructive?
I would like to be able to recover all I can before I start "fixing" the disk.
I also tried using different superblocks but I always get this message.

I tried mounting read-only but it didn't work.
> # mount -o ro /dev/sdc1 /hdd_a_917GB/
 
# ls /hdd_a_917GB/
[3786.593656] EXT2-fs error (device sdc1): ext2_readdir: bad page in #2
ls: reading directory /hdd_a_917GB/: Input/output error
 
(I tried accessing a known directory on my disk)
# ls /hdd_a_917GB/some_dir/
[3854.013562] EXT2-fs error (device sdc1): ext2_check_page: bad entry in directory #2 : rec_len is smaller than minimal - offset=0, inode=0, rec_len=0, name_len=0
ls: cannot access /hdd_a_917GB/some_dir/: No such file or directory

If I try to use debugfs to get any information...
> # debugfs -c -s 214990848 -b 4096 /dev/sdc1
debugfs 1.41.3 (12-Oct-2008)
/dev/sdc1: catastrophic mode - not reading inode or group bitmaps
debugfs:  ls /
/: EXT2 directory corrupted
debugfs:It doesn't matter if I pass the a superblock and block size, or not.



How can I recover my files before doing destructive actions with fsck?
And what are the implications of each possible answer to the question:
Resize inode not valid.  Recreate<y>?

BTW, I also ran smartctl -t short /dev/sdc and I got no errors.

---

### Post by kung fu buntu on 2009-06-18
*bumpy*
(sorry but this is really heart breaking :()

---

### Post by bodhi.zazen on 2009-06-18
Make sure the partition is not mounted or if this is the root file system, use a live Cd.

Then try (change /dev/sda1 to your actual partition of course): 

```
fsck -y /dev/sda1
```

If that fails

```
fsck /dev/sda1
```

If that fails

```
e2fsck -b 32768 -B 4096 /dev/sda1
```

If that fails re-boot and try to mount the partition again.

If that fails we will need something such as testdisk or photorec

---

### Post by HermanAB on 2009-06-18
Hmm, I would make a byte-wise copy of the disk first using 'dd' and try to recover the copy, not the original, since a recover operation can make things worse.

---

### Post by kung fu buntu on 2009-06-18
Thanks for the reply.

I have tried:
```
#e2fsck /dev/sdc1
e2fsck 1.41.3 (12-Oct-2008)
Resize inode not valid. Recreate<y>?
```
And stopped here by hitting ctrl+c.
My fear is that this will start a "self-destruct" on the drive. I don't know exactly what are the implications of this by either answering no or yes. Hence I would like to recover my data before I start a "write" behaviro on the disk.


"fsck -y" is just a say "yes" to all... which can possibly lead to data loss, that could be avoided by a "read only" approach.
I would like to "back up" before "fixing".

Considering I can't even get my way through debugfs, things don't bode well :(

I've tried giving other superblocks, but the result was the same.

Thanks for the tips on testdisk and photorec. I'll try them.

---

### Post by kung fu buntu on 2009-06-18
> **HermanAB said:**
> Hmm, I would make a byte-wise copy of the disk first using 'dd' and try to recover the copy, not the original, since a recover operation can make things worse.
Yes. Hence my desire to first try a "read only" approach before hammering it with fsck.
I can't dd a 917GB system :(
It wasn't full by a long margin, but I had several GB there... dd is not an option.

---

### Post by bodhi.zazen on 2009-06-18
The blue pill or the red pill ?

If you wish to back up first, dd is probably the best choice, you can compress the resulting image.

[http://www.linuxweblog.com/dd-image](http://www.linuxweblog.com/dd-image)

If that is not an option, proceed with fsck or seek professional assistance =)

---

### Post by kung fu buntu on 2009-06-18
Testdisk didn't help.

When I get to the undelete option it says:
```
 1 * Linux                    1   0  1 121599 254 63 1953487935
Directory /

No file found, filesystem seems damaged.

```

I should note it finds all my partitions and also my superblocks.
It seems as if my inode to "/" got... lost  :x 


> **bodhi.zazen said:**
> [...] or seek professional assistance =)
Yes, from a shrink. I will need it if I can't recover my data :p

---

### Post by bodhi.zazen on 2009-06-18
You can try photorec

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

---

