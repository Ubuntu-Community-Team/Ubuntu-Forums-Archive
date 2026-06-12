---
title: "defragment"
date: 2006-01-11
forum: General Help
---

### Post by iAlta on 2006-01-11
Can I defragment my hdd?
I have tried difrent things, but nothing seams to work.

---

### Post by earobinson on 2006-01-11
I searched the forums for (defrag) and I found this: [http://www.ubuntuforums.org/showthread.php?t=114993&highlight=defrag](http://www.ubuntuforums.org/showthread.php?t=114993&highlight=defrag)

---

### Post by az on 2006-01-11
In general, you will only see fragmentation become a problem if you use up most of your disk space.   If you keep your disks less than 90 per cent full, you should not really see much fragmentation.

It is so insignificant that no one has made a defragmentation tool for ext3 filesystems.

---

### Post by tomski on 2006-01-11
if any files do fragment those files will be files that are accessed more often than others.
it also occurs at such a slow rate on a single user workstation that you dont need to even think about it but if you do run into it just put all files that are accessed more often than others on a seperate disk, no need for tools!

---

### Post by tomski on 2006-01-24
for those interested here is an in-depth doc i created about this as a few of my freinds were interested too:
(Note i have taken some of this content from other sources) 



                Do I need to defrag the HD in Linux?  
If yes, how?
Short answer: No 
Long answer: 

In a single-user, single-tasking OS, it's best to keep all blocks for a file together, because _most_ of the disk accesses over a given period of time will be against a single file. In this scenario, the read-write heads of your HD advance sequentially through the hard disk. In the same sort of system, if your file is fragmented, the read-write heads jump all over the place, adding seek time to the harddisk access time.

In a multi-user, multi-tasking, multi-threaded OS, many files are being accessed at any time, and, if left unregulated, the disk read-write heads would jump all over the place all the time. Even with 'defragmented' files, there would be as much seek-time delay as there would be with a single-user single-tasking OS and fragmented files.

Fortunately, multi-user, multi-tasking, multi-threaded OS’s are usually built smarter than that. Since file access is multiplexed from the point of view of the device (multiple file accesses from multiple, unrelated processes, with no order imposed on the sequence of blocks requested), the device driver reorders the requests into something sensible for the device (i.e elevator algorithm).

In other words, fragmentation is a concern when one (and only one) process access data from one (and only one) file. When more than one file is involved, the disk addresses being requested are 'fragmented' wrt the sequence that the driver has to service them, and thus it doesn't matter to the device driver whether or not a file was fragmented.

To illustrate:

I have two programs executing simultaneously, each reading two different files.

The files are organized sequentially (unfragmented) on disk...

 [1.1][1.2][1.3][2.1][2.2][2.3][3.1][3.2][3.3][4.1][4.2][4.3][4.4]

Program 1 reads file 1, block 1
                file 1, block 2
                file 2, block 1
                file 2, block 2
                file 2, block 3
                file 1, block 3

Program 2 reads file 3, block 1
                file 4, block 1
                file 3, block 2
                file 4, block 2
                file 3, block 3
                file 4, block 4

The OS scheduler causes the programs to be scheduled and executed such that the device driver receives requests

                file 3, block 1
                file 1, block 1
                file 4, block 1
                file 1, block 2
                file 3, block 2
                file 2, block 1
                file 4, block 2
                file 2, block 2
                file 3, block 3
                file 2, block 3
                file 4, block 4
                file 1, block 3

Graphically, this looks like...

  [1.1][1.2][1.3][2.1][2.2][2.3][3.1][3.2][3.3][4.1][4.2][4.3][4.4]
}------------------------------>[3.1]
  [1.1]<-----------------------'
       `-------------------------------------->[4.1]
       [1.2]<---------------------------------'
            `----------------------->[3.2]
                 [2.1]<-------------'
                      `---------------------------->[4.2]
                      [2.2]<-----------------------'
                           `------------->[3.3]
                           [2.3]<-------'
                                `---------------------------->[4.4]
             [1.3]<------------------------------------------'

As you can see, the accesses are already 'fragmented' and we haven't even reached the disk yet. I have to stress this, the above situation is _no different_ from an MSDOS single file access against a fragmented file.

So, how do we minimize the effect seen above? If you are MSDOS, you reorder the blocks on disk to match the (presumed) order in which they will be requested.

OTOH, if you are Linux, you reorder the _requests_ into a regular sequence that minimizes disk access. You also buffer most of the data in memory, and you only write dirty blocks. In other words, you minimize the effect of 'disk file fragmentation' as part of the other optimizations you perform on the _access requests_ before you execute them.

Now, this is not to say that 'disk file fragmentation' is a good thing. It's just that 'disk file fragmentation' doesn't have the *impact* here that it would have in MSDOS-based systems. The performance difference between a 'disk file fragmented' Linux file system and a 'disk file unfragmented' Linux file system is minimal to none, where the same performance difference under MSDOS would be huge. 

Under the right circumstances, fragmentation is a neutral thing, neither bad nor good. 
As to defraging a Linux filesystem (ext2fs), there are tools available, but (because of the design of the system) these tools are rarely (if ever) needed or used.
That's the impact of designing up front the multi-processing/multi-tasking multi-user capacity of the OS into it's facilities, rather than tacking multi-processing/multi-tasking multi-user support on to an inherently single-processing/single-tasking single-user system.

However, contiguous file system block allocation will eventually end up with file blocks fragmented across the file system, and file system  access will eventually revert back to a random nature".

The question is, when is 'eventually'. If the filesystem is, at one time, quite full and you delete random files (randomly paced, that is), you will of course get high fragmentation. Every filesystem is affected by this fragmentation (ok, there's bound to be exceptions, but anyway), the question is: how bad, and how soon.


Measuring performance on a multi-user system is very complicated, because different users access different disk blocks, effectively producing fragmentation from the viewpoint of the filesystem driver asked to go get those blocks.

So if (simplified, multiply by 50 users or whatever)

Bob wants disk block 37550
Mary wants 37654
and Gene needs 28756, 

all at the same (relative time, that's the same as Paul, sitting alone at the machine, reading a fragmented file.

In both cases, good drivers and good hardware (SCSI) are going to rearrange the requests to be as efficient as possible,  

OTOH, if this machine is a database server, where client requests go through a central program, fragmentation *might* matter more, depending on the db server software- all else being equally confused as above. All "fragmented" drives are better than "unfragmented" ones on a multi-user multitasking o/s. 

The point is that the machine is doing many things simultaneously, so it has to jump around even if one task is interested in only one file. There will be up to a hundred tasks doing I/O simultaneously.

Yes, all disk drivers use elevator algorithms, in any o/s.

But to answer the question, ext2s spreads blocks out evenly through the disk, using various strategies (well, a single mixed strategy). This reduces the average seek time on a single elevator pass.

The term "Linux filesystems" is a little misleading. 
 e2fs doesn't generally have fragmentation issues, for certain definitions of "fragmentation."

The short answer is this: 
e2fs splits the disks up into block groups, which are contiguous regions of blocks.  The group will contain a certain number of inodes and (data) blocks.  When you create an inode, Linux probably chooses the group with the largest number of free (data) blocks.  When you write to an inode, Linux will preferentially allocate (data) blocks in the same group as the inode.  When it has to, it will move on to another (later) group, but will still try to keep the blocks together.

The end result of this is that data is generally fragmented by only a few blocks, and almost always travels in the same direction.  That's as opposed to the front-to-back fragmentation which could, and frequently did, occur in FAT and its derivatives.

The above works great until the file system is nearly full, at which point free blocks are scattered all across the disk is discontinuous locations.  This is why, on a nearly-full file system (above 95% or so), e2fs performance will degrade _substantially_.

Other file systems (HPFS/NTFS in particular) are similar, but call groups "bands" or "stripes" instead.  HPFS is actually worse than e2fs when nearly full, because it uses pseudo B-trees for the directory structure which periodically need to be rebalanced.  The problem there is that, when the file system is nearly full, directories may need to
be rebalanced into many different groups, which will obviously cause enormous slowdowns. e2fs uses a crummy, Palaeolithic array for its directories, which results in far worse performance overall, but wins out in this one narrow case (or can, depending on what's done to the directory).

So with all that information onboard when we use a multi-user system we may want to try & contain the fragmentation of ‘Often-modified files’ because often-modified files contribute heavily to fragmentation. So the best way to contain fragmentation is to store often-modified files on their own partition. That way, the other partitions are unaffected by the fragmentation caused by the heavily modified files and this may also provide a performance option in single-user systems. In concept, this is easy to understand, but how do you actually go about doing it? 
First, you must create a new partition for the specific purpose of storing frequently modified files. You might want to locate this partition on a separate disk to enhance performance.

METHOD:

1. Create a filesystem on the new partition

 Create a new partition that's big enough to hold /var and /tmp, with a little extra space left over. You'll need either an additional drive, or a spare (unused) partition that will house the often-modified files. If you do need to use fdisk or cfdisk to create the partition, you'll need to reboot once. Then, it's time to format the new partition as follows (it's OK to be in multiuser mode while you do this; I'll let you know when to switch to single-user):

# mkfs.ext2 /dev/???

2. Mount it to /mnt/rwstorage
??? should be replaced with the device name for the new, empty partition that you are creating. Accidentally typing the wrong name will destroy data on an existing partition, so be careful! After typing this command, you'll have a brand-new ext2 filesystem on the new partition. We're almost ready to mount it, but first, let's make a new mount point. 
# mkdir /mnt/rwstorage

I chose the name rwstorage to remind us that this particular partition is going to be specifically used to house files that are read from and written to frequently. To mount the partition, type:

# mount /dev/??? /mnt/rwstorage


3. Creating a new /tmp
The partition is now mounted and we're ready to create our new /tmp directory: 

# cd /mnt/rwstorage
# mkdir tmp
# chmod 1777 tmp

4. Drop to single-user mode

Our new directory at /mnt/rwstorage/tmp has the right permissions for a temporary directory. Now, drop to single-user mode, since we must copy over /var. As usual, we've delayed our drop to single-user mode to the last possible moment. Right now, we don't want any programs reading or writing files in /var, so we have to stop all daemons, disconnect all users, and do some quick maintenance by typing:

# init 1

If you're prompted to enter a password to perform system maintanance, do so. You should now have a root shell, and all unnecessary daemons will be stopped. Create a new location for our /var files by typing:


# cd /mnt/rwstorage
# mkdir var

5. Copy /var
Default permissions on our new /mnt/newstorage/var directory should be correct, so now we're ready to copy all of our original /var data over to the new partition:

# cd /var 
# cp -ax * /mnt/rwstorage/var

6. Back up and create symlinks

After this command completes, you'll have an exact copy of /var at /mnt/rwstorage/var. Now, you may be asking how exactly we get Linux to use /mnt/rwstorage/var and /mnt/rwstorage/tmp instead of the defaults in the root directory. This is easily done by the use of symbolic links -- we'll create the new symbolic links, /tmp and /var, which point to the correct directories in /mnt/rwstorage. First, let's back up the original directories:


cd /
# cp var var.old
# cp tmp tmp.old


The last line probably isn't necessary, since it's very likely that you don't have anything important in /tmp, but we're playing it safe. Now, let's create the symlinks:


# cd /
# ln -s /mnt/rwstorage/var /var
# ln -s /mnt/rwstorage/tmp /tmp


7. Finishing touches to /etc/fstab

Now, when any user or program uses /var, they'll automatically be transported to /mnt/rwstorage/var! Likewise for /tmp. We have one step left; however, it can be safely performed in multiuser mode. It's time to get Apache running again, and to allow all your users to log back in. Exit from runlevel 1 by pressing CTRL-D. The system should start up normally. Log in as root. 
The final thing we must do is configure /etc/fstab so that /dev/??? is mounted at /mnt/rwstorage. You must add a line like the following to your /etc/fstab: 

/dev/???   /mnt/rwstorage   ext2   defaults   1   2

Important: If you are using a kernel version in the 2.3+ range, it's very likely that you have a line in your /etc/fstab that looks like this:

none   /var/shm   shm   defaults   0   0

This line enables shared memory on your system, and by default it gets mounted in /var. In order for this line to work properly, it must appear after the line you just added. That way, when Linux starts up, /mnt/rwstorage will get mounted first (enabling /var). Then, and only then, will the shm device get mounted at /var/shm, which is really /mnt/rwstorage/var/shm. Make sure the lines are in this order:

/dev/???        /mnt/rwstorage  ext2    defaults       1     2
none            /var/shm        shm     defaults       0     0


After saving the changes to /etc/fstab, your system has been successfully upgraded! After verifying that everything is working properly, you'll want to remove the /tmp.old and /var.old backup directories. Congratulations -- you've successfully reconfigured your system's partitions for optimum performance.
                                                                                                           :END METHOD


Then again it is far easier to just wipe out the File system and restore from backups but where is the fun in that!!!  

T&#937;  R&  ©2006

---

