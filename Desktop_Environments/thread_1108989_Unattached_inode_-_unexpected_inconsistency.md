---
title: "Unattached inode - unexpected inconsistency"
date: 2009-03-28
forum: Desktop Environments
---

### Post by BioGeek on 2009-03-28
Hey all,

When I start up, my Ubuntu Jaunty gives at the splash screen

```
unclean shutdown, checking drives
```

and then

```
/dev/sda1: UNEXPECTED INCONSISTENCY: RUN fsck MANUALLY 
        (i.e. without -a or -p options)
fsck died with exit status 4
Checking drive /dev/sda1: 93% (stage 4/5, 568/1147)
                                                        [fail]
* An automatic file system check (fsck) of the root filesystem failed. 
A manual fsck must be performed, then the system restarted. 
The fsck should be performed in maintenance mode with the root filesystem in read-only mode.
* The root filesystem is currently mounted in read-only mode. 
A maintenance shell will now be started.
After performing system maintenance,press CONTROL-D to terminate
 the maintenance shell and restart the system.
bash: no job control in this shell
```

But when I do that, my system starts screaming at me:

```
root@phalacrocorax:~# fsck -v /dev/sda1
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
/dev/sda1 contains a filesystem with errors, check forced
Pass 1: checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Unattached inode 4653163
Connect to /lost+found<y>? yes

WARNING: PROGRAMMING BUG IN E2FSCK!
         OR SOME BONEHEAD (YOU) IS CHECKING A MOUNTED (LIVE) FILESYSTEM
inode_link_info[4653163] is 65500,inode.i_links_count is 65535. They should be the same!
Inode 4653163 ref count is 65535, should be 1. Fix<y>?
```

What should I do now?

---

### Post by BioGeek on 2009-03-29
Pressing 'yes' to all the questions that popped up solved my problem.

Still don't know what exactly happend, what caused the problem, or how I can prevent it in the future.

---

