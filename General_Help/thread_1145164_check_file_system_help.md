---
title: "check file system help"
date: 2009-05-01
forum: General Help
---

### Post by omskates on 2009-05-01
Please help with a hint into the right direction, anyone.  Thanks!

Log of fsck -C -R -A -a 
Fri May  1 08:34:16 2009

fsck 1.41.3 (12-Oct-2008)
fsck.ext3: Unable to resolve 'UUID=55d36f34-20c5-41d4-9f6b-6cc9c990098e'
/dev/sda5: clean, 44/32576 files, 19572/118479 blocks
/dev/sda8: clean, 49107/13861088 files, 1878772/55743534 blocks
/dev/sda6: clean, 9022/512000 files, 536533/2048001 blocks
fsck died with exit status 8

prompts to check file system manually.  I have used partition editor to check and repair but no improvement.

---

### Post by taurus on 2009-05-01
Are you able to boot Ubuntu at all?  If you still can, open a terminal and post the outputs of these commands.

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by omskates on 2009-05-01
Thank you for your reply!



Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x02a802a7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1640    13173268+  83  Linux
/dev/sda2            1641       30401   231022732+   5  Extended
/dev/sda5            2202        2260      473917+  83  Linux
/dev/sda6            2261        2515     2048256   83  Linux
/dev/sda7            2516        2642     1020096   82  Linux swap / Solaris
/dev/sda8            2643       30401   222974136   83  Linux
/dev/sda9            2151        2201      409626   83  Linux

Partition table entries are not in disk order

---

### Post by zero7404 on 2009-05-01
i decided to run an fsck inquery to see if my installation is good and i get a whole bunch of fix prompts for different kinds of errors...but my installation starts up fine.

i was wanting to do an fsck -p, but i got a warning message saying i shouldn't do it on a mounted file system....so i aborted.

i'd like to know that my install is healthy and running without disk errors, much like i do my disk checks and defrags in windows, but i don't want to mess up the installation....

can i get advice on how to successfully and safely run fsck once in a while, to keep the disk optimal ?

---

### Post by omskates on 2009-05-01
I would be happy with a link to fsck tutorial as well as feedback on my fdisk output as seen above.
Thanks:)

---

### Post by lensman3 on 2009-05-01
1) boot up in single user mode.  One of the boot options is repair mode or add "single" to the first line of grub.  This will boot the OS with only one process running.  Eventually you will get to a # prompt.

2) Do a "df" to see the paritions. And for each partition do " mount -n -o remount,ro <filesystem>". Each file system that was displayed in the "df" command needs to have this  mount command run against it.  The way to prove that a file system is read-only is to use the touch command.  In whatever directory you are in do a "touch junk-file".  If the file system is read-only, then the file will not be created.  

3) Run the fsck command.  "fsck -y -f <file-system>".  The -y is for answering yes to all problems with the file system, and -f is to force a check.  There is a bit in the disk header that flags whether the filed  system has been "fsck"ed.  I would suggest that the file-system be checked at least twice.  The -y answer is a real gotcha.  Unless you know how to fix the inodes and know exactly the numbers to enter, let "fsck" do it's stuff.  At this point there is not much you can do.  I don't think that the author of the ext3 file-system knows what to enter.

4)  Repeat 2) and 3) until all partitions are done.  You generally don't need to check the swap and partition 4 which is the extended partition.  The  extended partition 4 points to all partitions of 5 and above.

5) When you go into single user mode, the partition that you are dumped to is "/" - root.  If you are on the root partition, generally the mount to read-only won't let you mount it read-only because you are a directory on that partition.  "cd" to another partition such as /boot.  Now try the mount command again and see if it will go read-only.  TO SEE WHICH FILE SYSTEM YOU ARE CURRENTLY IN USE THE "df ." command (Notice the trailing dot).

6) Generally it is OK to type a "CNTL-c" to kill a running fsck. It will eventually stop.  If you don't use the -y flag, then be prepared to type "yes"  or "y" a lot.  It is OK to CNTL-c here and restart with the -y flag.  

I hope this helps.

---

### Post by omskates on 2009-05-02
Thanks much! I will work with that and see what I can do.

---

