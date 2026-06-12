---
title: "kernel leak? + corrupt filesystem"
date: 2005-12-25
forum: General Help
---

### Post by ZylGadis on 2005-12-25
I think this thread does not belong here, as it is not specific to Gnome. However this is the best place I could find to post it. Please move it if necessary.
Here is the situation, describing two problems:
A few (three, I think) days ago a new version of the kernel was released in the reps, and I duly updated all ubuntu computers at home (laptop and two desktops). No other updates have been done to any of them.
A day later the laptop would not log into Gnome - GDM said something about not being able to write to some file. Possible reasons: no write permissions or disk full. I went into console mode and df showed that, indeed, the disk was full, even though it had had about 4GB free space the day before.
I fiddled with files a bit and found the cause of the problem - three of the system log files (syslog and two others) in /var/log were 1.3GB each, thus filling all of the space on the drive. Unfortunately I did not take a look at them before deleting them, so I can't be certain the new kernel is guilty. Having in mind that nothing else had been done to the system, though, that is the apparent cause.
It needs to be said that none of the other two Ubuntu computers at home have had this problem.

Onto the second one: after deleting log files with pipes to them still open, of course I rebooted and ran e2fsck in read-only mode. The root filesystem had some errors. I forced a boot check, but fsck fixed nothing after rebooting. Going to single-user mode and remounting read-only does not work, it says "/ is busy" or something. Next step would be to find a live cd and try booting and fixing from there.
Anyway, the more important part here is that every Ubuntu computer at home has errors, and none are fixable after running a bootcheck. I don't know how dangerous that is, or how relevant to the kernel problem, but I think we have a situation here, especially if other people do fsck and report similar things.
Here is a screenshot of e2fsck on one of the desktops:

```
alex@woof:~$ e2fsck
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
alex@woof:~$ e2fsck -n /dev/hda2
e2fsck 1.38 (30-Jun-2005)
Warning!  /dev/hda2 is mounted.
e2fsck: Permission denied while trying to open /dev/hda2
You must have r/o access to the filesystem or be root
alex@woof:~$ sudo e2fsck -n /dev/hda2
Password:
e2fsck 1.38 (30-Jun-2005)
Warning!  /dev/hda2 is mounted.
Warning: skipping journal recovery because doing a read-only filesystem check.
/ contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Free blocks count wrong (6583640, counted=6583316).
Fix? no

Free inodes count wrong (3586465, counted=3586400).
Fix? no


/: ********** WARNING: Filesystem still has errors **********

/: 92735/3679200 files (0.8% non-contiguous), 766097/7349737 blocks

```

Again, running e2fsck on the other systems shows similar things, and none are fixable with a bootcheck.

I have no idea how serious these two issues are, but I think it is useful to report them :)

---

