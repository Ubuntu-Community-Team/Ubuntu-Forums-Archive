---
title: "Problems mounting partition"
date: 2009-02-10
forum: General Help
---

### Post by Ant01 on 2009-02-10
Can someone please help me, I am having problems mounting a partition. Initially it was formated as a windows NTFS partition. I reformated the partition to ext2 but am still having the same problem.

I posted a thread earlier "[COLOR="Red"][Problems mounting windows partition]("http://ubuntuforums.org/showthread.php?t=1063146")[/COLOR]" but still have had no luck

Is the a fsdsk in Ubuntu that I can run that may sort out the problem or is it something else?

---

### Post by cmnorton on 2009-02-14
Are you expecting the partition to mount automatically, or do you want to mount and dismount the partition on demand? 

Do you have a mount directory created in /media?

What happens when you enter the mount command?

---

### Post by Ant01 on 2009-02-15
> **cmnorton said:**
> Are you expecting the partition to mount automatically, or do you want to mount and dismount the partition on demand? 

Do you have a mount directory created in /media?

What happens when you enter the mount command?

I have a mount directory in /media and it seems to mount when I run the command, I get no errors. If I run the command again its says the partion is mounted already but when I look for the directory I can't find the partition

---

### Post by cmnorton on 2009-02-15
What is the output of df?

This sounds like you need to mount the directory with the proper file system in the mount command.

---

### Post by Ant01 on 2009-02-16
I umounted the partition and remounted it on /media/sbd1 as you can see, but still can't see drive

[IMG]http://i254.photobucket.com/albums/hh118/AntoineMuskat/Ubunyu3.jpg?t=1234770280[/IMG]

---

### Post by vanadium on 2009-02-16
This looks like you correctly mounted the drive on /media/sdb1. If you navigate to /media/sdb1, you should see the contents of the drive. You will not be able to write to that drive as a normal user, though, unless you grant yourself permissions.

---

### Post by Ant01 on 2009-02-16
> **vanadium said:**
> This looks like you correctly mounted the drive on /media/sdb1. If you navigate to /media/sdb1, you should see the contents of the drive. You will not be able to write to that drive as a normal user, though, unless you grant yourself permissions.

I still don't understand why I can't see the drive as a mounted drive? How do I grant permission to write to the folder and can I share it with my windows network as I want to backup to that folder?

Thanks for the help.

---

### Post by vanadium on 2009-02-16
The particular nature of your problem is not clear. Yoru command line output indicates that the drive is properly mounted. to make that sure, check the output of the command
```

mount

```
(see also first post of cmnorton).

Indeed, by default, you should see any drive mounted under /media as an icon on the desktop. However, that is a feature that can be turned off.

To grant a user permission to use the entire drive, change the ownership of the mount point (/media/sdb1).

b.t.w. you have two linux partitions on your sdb. Are you aware of that?

If you are not sure, then post the output here of the commands

```

sudo fdisk -l
sudo blkid
cat /etc/fstab
mount

```

---

### Post by Ant01 on 2009-02-16
I am stil new to ubuntu so am not to sure what to do, so I ran the commands that you suggested. Below is the output of the commands. 

I am not sure what you mean by "To grant a user permission to use the entire drive, change the ownership of the mount point (/media/sdb1)." and also (see also first post of cmnorton).

Copy of Transcript
[IMG]http://i254.photobucket.com/albums/hh118/AntoineMuskat/UbuntuCommands.jpg?t=1234800455[/IMG]

---

### Post by cmnorton on 2009-02-16
I believe what vanadium is saying is, as your regular user name, this mounted tree must have sufficient permissions, so that you can see the tree. When root (sudo) created the tree, the tree retained root's ownership and protections. You might not be able to see the tree if it is not protected correctly. 

If you should own the whole tree, then you would first enter this command.  

sudo chown -R your-user-name:your-user-name /media/48gig

If you only need to access the tree and not be the owner, then you need to mark this path with these permissions assuming this tree is owned by root:

chmod -R o=rx /media/48gig

If you need to write in this tree, add a "w" to the "rx" above.

---

### Post by vanadium on 2009-02-17
A comment before: to post output here, it is much easier to copy/paste the terminal output here. Not only for you, also for me. In the terminal, select the text, choose "Edit - Copy", then paste in your answer. Surround your output with the tags ```
{code}...here comes your output{/code}
```. Replace curly braces with rectangular braces!

There are errors in your /etc/fstab. Your sdb1 is announced there, but with wrong file system. Your sdb2 is not announced there, so won't automatically mount.

Open a terminal and execute following command to create a backup of your current /etc/fstab

```

sudo cp /etc/fstab /etc/fstab.backup

```
You will be asked for your login password. Provide it. You won't see anything on the screen while you type it: this is normal.
Open your /etc/fstab file with root permissions.
```

gksudo gedit /etc/fstab

```
Find the line 
```

/dev/sdb1 /media/Recoverable...

```
and delete it.
Add following lines at the end of the file
```

#/dev/sdb1
UUID="a1a39721-b143-43d2-9e54-d9f9ef2e2998" /media/sdb1 ext3 defaults 0 2
#/dev/sdb2
UUID="b29f0a4a-559d-43f8-941d-c3b06a5ff035" /media/sdb2 ext3 defaults 0 2

```
Save the file and exit gedit.

I am not sure your mount point /media/sdb2 exists, so create it (you will have a message if it already exists)
```

sudo mkdir /media/sdb2

```
Now reboot the system. After you have logged in again, open up the terminal and check wether your /etc/fstab is OK
```

sudo mount -a

```
If you do not see any output, your /etc/fstab is correct. If you do see output, there are errors. Then post the output here, along with the output of

```

cat /etc/fstab

```
which will allow us to correct remaining errors.

---

