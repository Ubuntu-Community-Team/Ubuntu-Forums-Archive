---
title: "What are the non-contiguous inodes?"
date: 2009-03-10
forum: General Help
---

### Post by El Potro on 2009-03-10
Hi everone,

I'm running ubuntu 8.10 and win xp in this machine, each one in it's own separated disk. The problem is, that I've installed an app in win that allows me to access and create files in the ext3 partitions as if they were windows-native. (The name of the free software is ***Ext2fsd***).

It works flawlessly but the thing is, that yesterday I got a blue screen after clicking an .exe file on windows, which was in a ext3 partition! So I rebooted and did it again... The blue screen again showed up!

Then back on ubuntu (I everytime have to wait for the disk checks that take a lot of time) but this time the disk check wasn't finished, because some problem was found... I don't remember exacty how I fixed it, but I remember I ran fsck in the partition that was found with problems, and after pressing "yes" a couple of times, all was fixed.

Today, I just did ```
fsck -C -c -r -v /dev/sda6
``` and this is what it showed me back:

```
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
Checking for bad blocks (read-only test): done                                
/docs: Updating bad block inode.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure                                           
Pass 3: Checking directory connectivity                                        
Pass 4: Checking reference counts
Pass 5: Checking group summary information                                     
                                                                               
/docs: ***** FILE SYSTEM WAS MODIFIED *****

   40423 inodes used (0.54%)
    2119 non-contiguous inodes (5.2%)
         # of inodes with ind/dind/tind blocks: 26158/5834/0
22425592 blocks used (75.54%)
       0 bad blocks
       1 large file

   39298 regular files
    1107 directories
       0 character device files
       0 block device files
       0 fifos
       0 links
       9 symbolic links (9 fast symbolic links)
       0 sockets
--------
   40414 files

```

I'm concerned about what the heck are the non-contagious inodes? and if they're something that's bad in my system?

I have a notion about what inodes are, but I never heard of non-contagious inodes.

Can anybody help?

Thank you very much,

Mauricio

---

### Post by Yellow Pasque on 2009-03-10
Non-contiguous inodes are files that are physically split up on your hard disk. This is similar to fragementation. It occurs naturally on ext3 filesystems and is not "harmful", but may slow your system down a little if there's too much of it.
[http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)

As for your problem, it's probably a bug or inherent limitation of running ext2fsd. Question: Why are you trying to run Windows .exe files stored on an ext2/3 volume?

---

### Post by El Potro on 2009-03-10
If it is so how to defragment? Or what's the way to solve the problem so that the system runs "smoother"? Is there any way?


> Question: Why are you trying to run Windows .exe files stored on an ext2/3 volume? 

I was just arranging some files that I saved up from an old disk, and some of them were windows executables.

I know I should have copied them to a fat partition before running them, but... it should work, I wasn't planning leaving them in no other partition than the /home one. I was running them on windows just for knowing which application works and which not. (since I can't trust wine this, because it is old software).

Thanks for helping!

---

### Post by Yellow Pasque on 2009-03-10
There's no native defragment tool for ext3. Read the link I gave above if you are really concerned about it.

> Modern Linux filesystem keep fragmentation at a minimum by keeping all blocks in a file close together, even if they can't be stored in consecutive sectors. Some filesystems, like ext3, effectively allocate the free block that is nearest to other blocks in a file. **Therefore it is not necessary to worry about fragmentation in a Linux system.**
[http://www.tldp.org/LDP/sag/html/filesystems.html](http://www.tldp.org/LDP/sag/html/filesystems.html)

---

### Post by El Potro on 2009-03-11
Thank you Temüjin,

I'm looking forward to Ubuntu 9.04 with ext4 support.

---

