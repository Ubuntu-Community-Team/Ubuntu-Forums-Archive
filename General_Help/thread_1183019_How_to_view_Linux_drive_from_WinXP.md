---
title: "How to view Linux drive from WinXP"
date: 2009-06-09
forum: General Help
---

### Post by Ripplinger on 2009-06-09
I'm a very new user to Linux and installed Ubuntu 9.04 on its own 120GB hard drive.  Most everything setup pretty easily, networking, sound, just a few minor hardware issues to iron out.  I can access the WinXP drives on the system through Ubuntu, and can also access the 2 other networked PCs with WinXP on them. 

When I boot back into WinXP though, I can't view the Linux 120GB drive.  At first I couldn't even see it other than in Disk Manager, but Disk Manager wouldn't let me assign a drive letter.  I installed Ext2IFS_1_11a.exe and that let me assign drive letters to the Linux drive, but when I try to view the contents through windows explorer it says the drive needs to be formatted.

The Ext2 site had me run mountdiag.exe and it gave me this info:
> The volume has an Ext2/Ext3 file system, but the Ext2 IFS 1.11 software did not mount it because the file system has an inode size unequal to 128 bytes (inode size:  256 bytes).

The only way to solve it is to back up the volume's files and format the file system:  give the mkfs.ext3 utility the -I 128 switch.  Finally, restore all back-up files.

After that, the Ext2 IFS software should be able to access the volume.And then I was lost.   Is there an easier way to get WinXP to be able to read/write (or I'd even be happy to just read) to the Linux drive? 

Thanks for any help.

---

### Post by synapsys on 2009-06-09
Windows does not natively support linux or mac filesystems....ext2/3/4, hfs, etc....
For this you need to use a program inside windows that is meant to be able to do this.

Check this out:
[http://www.howtoforge.com/access-linux-partitions-from-windows](http://www.howtoforge.com/access-linux-partitions-from-windows)

---

### Post by Ripplinger on 2009-06-09
None of those worked for me, I'm guessing it's the issue I quoted in my original post where it said the only way to fix the problem is to reformat the Linux drive:  "The only way to solve it is to back up the volume's files and format the file system: give the mkfs.ext3 utility the -I 128 switch. Finally, restore all back-up files."

That's probably what I need more specific instructions to do, what is the exact command I would use to format the Linux drive.  

Once that's done, is it just a matter of copying over the files back to the Linux drive then or must Ubuntu be reinstalled again?  And if reinstalled, will it keep the new formatting?

---

