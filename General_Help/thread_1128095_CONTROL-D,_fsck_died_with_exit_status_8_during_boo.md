---
title: "CONTROL-D, fsck died with exit status 8 during bootup"
date: 2009-04-17
forum: General Help
---

### Post by sponsoredwalk on 2009-04-17
fsck.ext3 unable to resolve 'UUID=bea292d9-0c18-45c1-84b1-021c84247b1b'
fsck died with exit status 8

File system check failed 
a log is being saved in your /var/log/fsck/checkfs if that location is writable
please repair the file system manually
a maintenance shell will now be started
CONTROL-D will terminate the shell and resume system boot

-------------------------------------------------------------
When i start up my computer the above message comes up halfway through the loading bar on my UBUNTU 7.10 system, i must press control & d together to continue to the splash screen to log on, i'm curious can this be fixed as it is such an inconvenience.

---

### Post by meeko on 2009-04-17
Try running e2fsck, as that may solve the problem. That's actually more of a guess though. I've never seen that message before.

---

### Post by sponsoredwalk on 2009-04-17
:~$ fsck
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
/dev/sdb3 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? no

check aborted.
e2fsck 1.40.2 (12-Jul-2007)
/dev/sdb1 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? no

check aborted.
fsck.ext3: Unable to resolve 'UUID=bea292d9-0c18-45c1-84b1-021c84247b1b'


when i type e2sfck i get :
e2fsck
Usage: e2fsck [-panyrcdfvstDFSV] [-b superblock] [-B blocksize]
                [-I inode_buffer_blocks] [-P process_inode_size]
                [-l|-L bad_blocks_file] [-C fd] [-j external_journal]
                [-E extended-options] device

Emergency help:
 -p                   Automatic repair (no questions)
 -n                   Make no changes to the filesystem
 -y                   Assume "yes" to all questions
 -c                   Check for bad blocks and add them to the badblock list
 -f                   Force checking even if filesystem is marked clean
 -v                   Be verbose
 -b superblock        Use alternative superblock
 -B blocksize         Force blocksize when looking for superblock
 -j external_journal  Set location of the external journal
 -l bad_blocks_file   Add to badblocks list
 -L bad_blocks_file   Set badblocks list



?????????????????????????????????????????????????????????????????

---

### Post by meeko on 2009-04-17
Well, you're getting that error because fsck thinks your file systems are corrupted.  The only way that I know of to repair a corrupted file system is by using e2fsck.  Obviously if it fails in repairing them, there could be damage.  If you want, wait to see if more ideas surface, but that's the only way I know how to attempt to repair a corrupted file system.

---

### Post by suresh_vandiyur on 2009-04-17
> **sponsoredwalk said:**
> fsck.ext3 unable to resolve 'UUID=bea292d9-0c18-45c1-84b1-021c84247b1b'
fsck died with exit status 8

File system check failed 
a log is being saved in your /var/log/fsck/checkfs if that location is writable
please repair the file system manually
a maintenance shell will now be started
CONTROL-D will terminate the shell and resume system boot

-------------------------------------------------------------
When i start up my computer the above message comes up halfway through the loading bar on my UBUNTU 7.10 system, i must press control & d together to continue to the splash screen to log on, i'm curious can this be fixed as it is such an inconvenience.
run fsck..  select yes...

---

### Post by sponsoredwalk on 2009-04-17
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
/dev/sdb3 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? yes

/dev/sdb3: recovering journal
Clearing orphaned inode 20825013 (uid=1000, gid=1000, mode=0100600, size=28700)
Clearing orphaned inode 4088038 (uid=116, gid=129, mode=0100600, size=0)
Clearing orphaned inode 4088022 (uid=116, gid=129, mode=0100600, size=0)
Clearing orphaned inode 4088018 (uid=116, gid=129, mode=0100600, size=0)
Clearing orphaned inode 4088017 (uid=116, gid=129, mode=0100600, size=0)
Clearing orphaned inode 4088014 (uid=116, gid=129, mode=0100600, size=0)
/dev/sdb3: clean, 530871/36563072 files, 67994926/73242343 blocks
e2fsck 1.40.2 (12-Jul-2007)
/dev/sdb1 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? yes

/dev/sdb1 was not cleanly unmounted, check forced.
Pass 1: Checking inodes, blocks, and sizes

Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sdb1: 45/245280 files (20.0% non-contiguous), 87607/489951 blocks
fsck.ext3: Unable to resolve 'UUID=bea292d9-0c18-45c1-84b1-021c84247b1b'


this was my output when i did it ^

---

### Post by suresh_vandiyur on 2009-04-17
> **sponsoredwalk said:**
> fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
/dev/sdb3 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? yes

/dev/sdb3: recovering journal
Clearing orphaned inode 20825013 (uid=1000, gid=1000, mode=0100600, size=28700)
Clearing orphaned inode 4088038 (uid=116, gid=129, mode=0100600, size=0)
Clearing orphaned inode 4088022 (uid=116, gid=129, mode=0100600, size=0)
Clearing orphaned inode 4088018 (uid=116, gid=129, mode=0100600, size=0)
Clearing orphaned inode 4088017 (uid=116, gid=129, mode=0100600, size=0)
Clearing orphaned inode 4088014 (uid=116, gid=129, mode=0100600, size=0)
/dev/sdb3: clean, 530871/36563072 files, 67994926/73242343 blocks
e2fsck 1.40.2 (12-Jul-2007)
/dev/sdb1 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? yes

/dev/sdb1 was not cleanly unmounted, check forced.
Pass 1: Checking inodes, blocks, and sizes

Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sdb1: 45/245280 files (20.0% non-contiguous), 87607/489951 blocks
fsck.ext3: Unable to resolve 'UUID=bea292d9-0c18-45c1-84b1-021c84247b1b'


this was my output when i did it ^
how this Error was occuured? what will you did?...

---

### Post by sponsoredwalk on 2009-04-17
i only typed "y" as in, i answered yes to running fsck

---

### Post by meeko on 2009-04-17
I did some searching on the forums for you and this seems like a carbon copy of your issue: [http://ubuntuforums.org/showthread.php?t=654633](http://ubuntuforums.org/showthread.php?t=654633)

Let me know if that helps.

---

### Post by sponsoredwalk on 2009-04-17
I followed the instructions in the link you gave me, rebooted and i was again prompted for the CONTROL-D message. So there i gave my password for the maintenance shell instead and ran fsck which did the job for me, thanks so much for the help, means a lot :)

---

### Post by Bachstelze on 2009-04-17
Oh my...

> **sponsoredwalk said:**
> 
WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? yes

Wasn't the message clear enough? You can consider yourself extremely lucky if none of your data was lost. Don't do that again, *always* unmount a filesystem before [font="monospace"]fsck[/font]ing it (do it from a Live CD if you must).

---

