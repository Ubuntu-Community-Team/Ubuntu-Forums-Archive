---
title: "Random selected hard disk"
date: 2007-05-23
forum: Desktop Environments
---

### Post by ivoivo on 2007-05-23
Hello All,

First of all I would like to comment that I'm not a Linux newbie, using it since some 10 years now.

In my Dell desktop I have two identical IDE harddisks which are seen by Feisty  as sda and sdb.
On sdb I manually and regularly create a "dd" backup of sda.
sdb is marked with a # in /etc/fstab and even switched to "OFF" in the BIOS settings.
When I reboot my desktop it seems that the hardisks both can be randomly selected and thus being assigned sda or sdb.
For example, yesterday I created a directory under my homedir in which I downloaded the contents of my digicam. This evening I started my PC and the directory seems to be gone.
However, when I manually mount the sdb, the directory suddenly shows up there.
I'm struggeling with this for some weeks now and this evening I pulled the plugs from the second disk so there cannot be any mistake taken by the system.

I've tried to use both /etc/fstab versions, that is the old-style one without the UUID stuff and the new-style with the UUID, to no avail.
I think it's bizarre that while the disk is hashed in fstab and set to OFF in the BIOS the Linux kernel still can access it.

Does anyone recognize this problem and if so, is there a cure for it?

---

### Post by vandervyvere on 2007-05-29
I am also looking for a fix for this problem. I have created two raid arrays with mdadm. mdadm still picks up the created arrays but when the drives "swops around" fsck complains about the following:

[I]bread: Cannot read the block (2): (Invalid argument).
reiserfs_open: bread failed reading block 2
bread: Cannot read the block (16): (Invalid argument).
reiserfs_open: bread failed reading block 16

reiserfs_open: the reiserfs superblock cannot be found on /dev/md0.
Failed to open the filesystem.

If the partition table has not been changed, and the partition is
valid  and  it really  contains  a reiserfs  partition,  then the
superblock  is corrupted and you need to run this utility with
--rebuild-sb.[/I]

fsck died with exit status 8

I can recreate the file system, reboot the machine and it will boot up fine for about 6 or 7 boots max which after I get the same error.

Even with the error I can mount the raid fine and read it, the thing is that I would like to boot up UBUNTU with out errors.

---

