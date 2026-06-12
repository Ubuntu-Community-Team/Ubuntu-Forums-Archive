---
title: "fsck -f /dev/sdb1"
date: 2009-05-17
forum: General Help
---

### Post by ffixcollector on 2009-05-17
To maintain my file system I ran

```
fsck -f /dev/sdb1
```

on an hot-swat ext3 SATA drive, and got

[HTML]44299/61054976 files (7.2% non-contiguous), 157214113/244190000 blocks[/HTML]

What should I do now?
and
Is this a safe process to run after unmounting the drive?

What else can I do to maintain my externa drive? I have heard of tine2fs, but don't know how to properly use it.

---

### Post by ffixcollector on 2009-05-17
should I use
```
fsck -f -p /dev/sda1
```
to fix this?

---

### Post by Yellow Pasque on 2009-05-17
It is safe to run fsck manually. (Are you having issues with the drive?)

If the fsck completed successfully, do nothing.

If you're really curious about the reported fragmentation, see:
[http://en.wikipedia.org/wiki/Ext3#Defragmentation](http://en.wikipedia.org/wiki/Ext3#Defragmentation)
Ext3 keeps files close together, so even if they're technically "fragmented", the performance shouldn't noticeably suffer.

---

### Post by Locutus_of_Borg on 2009-05-17
that output is fine

tune2fs doesnt really fix or maintain a file system but just changes properties of it, like you can add a journal to an ext2 file system, change number of mounts before an auto-fsck is performed, etc.

If you really want, you can run badblocks on it, but e2fsck has a parameter in it that does the same thing

whenever i am concerned over a drives integrity, i run

```

e2fsck -fcckpv /dev/sda#

```

---

### Post by Yellow Pasque on 2009-05-17
> to fix this?

Fix what? :?

---

### Post by ffixcollector on 2009-05-17
> **Temüjin said:**
> Fix what? :?

The (7.2% non-contiguous) is what I am concerned about. Of course I understand that you will have non-contiguous files, but is this acceptable on a 1tb drive with 35% free space?

---

### Post by ffixcollector on 2009-05-17
> e2fsck -fcckpv /dev/sda#

What are the specifics on this command?

---

### Post by Yellow Pasque on 2009-05-17
-f = force fsck even if filesystem seems clean
-cc = run badblocks check with a non-destrutive test (might take a while on a 1 TB drive)
-k = write new list of badblocks to current list
-p = automatically repair errors if possible without requiring human input
-v = verbose output

---

### Post by ffixcollector on 2009-05-17
```
e2fsck -fcckpv /dev/sda# 
```
so this will check for badblocks, Fix them, and tell me how many and which ones are bad?

---

### Post by Locutus_of_Borg on 2009-05-17
> **ffixcollector said:**
> The (7.2% non-contiguous) is what I am concerned about. Of course I understand that you will have non-contiguous files, but is this acceptable on a 1tb drive with 35% free space?
7.2% non-contiguous is nothing to worry about
it means that 7.2% of your files are "fragmented" for lack of a better term

e.g.

suppose you have three files

aaa bbb ccc

as is, they are contiguous

aaa bbcbcc

this would be partially non-contiguous

bad example i know, but it just means that part of the data is not all together in a neat little line

it doesnt really affect anything thanks to the journal and how ext3 utilizes the block structure

compare this to ntfs where those three files might look like

abacgggbab          
gfhj

hjfghj
f


cjhjhgkg
c

plus there is no journal in ntfs file systems

---

### Post by Locutus_of_Borg on 2009-05-17
> **ffixcollector said:**
> ```
e2fsck -fcckpv /dev/sda# 
```
so this will check for badblocks, Fix them, and tell me how many and which ones are bad?
yeah essentially

it's good to run every once in a while, but generally the built-in fsck utility is enough to ensure your system is sane

---

### Post by ffixcollector on 2009-05-17
so how fragmented can a ext3 get before problems occur?

---

### Post by Locutus_of_Borg on 2009-05-17
you'll run out of disk space before that occurs

---

### Post by ffixcollector on 2009-05-17
Thank you Locutus_of_Borg and Temüjin this helped me out alot.

---

### Post by ffixcollector on 2009-05-18
Its been over 12 hours, and  <sudo e2fsck -fcckpv /dev/sdb1> is still running. Is this normal? there is no progress bar, or any description of what it is doing. The HDD activity lights have been on since it started. My boot HDD and external HDD

---

### Post by Yellow Pasque on 2009-05-18
If you're physically testing every block on a 1TB drive, it's going to take a while.

> On a Pentium 4 3GHz machine with one(1) gigabyte of ram and a single Seagate 80 gigabyte drive connected to a PATA 100 interface badblocks in the script above will take around two(2) hours to complete. A 250 gigabyte Maxtor drive connected to PATA 100 interface will take 9 hours and a 750 gigabyte Seagate drive connected to a SATA 133 interface will take 13 hours.
[https://calomel.org/badblocks_wipe.html](https://calomel.org/badblocks_wipe.html)

> P4 3.0GHz with PATA 133 250G 1 Drive == 8 hours
[http://www.pantz.org/software/badblocks/badblocksusage.html](http://www.pantz.org/software/badblocks/badblocksusage.html)

---

### Post by ffixcollector on 2009-05-18
Is there any way to run a more generic badblock scan that takes less time?

---

### Post by Yellow Pasque on 2009-05-18
AFAICT, badblocks is always going to take a long time. It's the price you pay for a massive amount of storage. However, you can run fsck without it, just like you were doing before. 

Run fsck often (every 30-40 mounts) and save badblocks for rare use, unless you're worried about the drive's physical integrity (i.e you dropped the drive and/or see evidence of data corruption).

---

### Post by ffixcollector on 2009-06-03
I have another question. My external SATA drive does not auto-mount on ubuntu startup. Will it automatically FSCK after the 15 mount count I set?

---

### Post by Yellow Pasque on 2009-06-03
> **ffixcollector said:**
> I have another question. My external SATA drive does not auto-mount on ubuntu startup. Will it automatically FSCK after the 15 mount count I set?
In my experience, it does not, though if you mount it from a terminal or look at dmesg right after mounting, you will get a recommendation to fsck the volume.

---

