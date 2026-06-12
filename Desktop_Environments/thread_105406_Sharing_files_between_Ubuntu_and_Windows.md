---
title: "Sharing files between Ubuntu and Windows"
date: 2005-12-18
forum: Desktop Environments
---

### Post by bakert on 2005-12-18
I'd like to set up a partition that is used as the main "data" area in both Ubuntu and Windows.

I've set up a dual boot Ubuntu and Win XP box.  I have also set up a data partition for storing shared files on.  I am planning on ditching Windows but have certain work commitments that require Windows for the medium term.

I used TweakUI in Windows to make the data partition contain My Documents, My Music, etc.

I'd like now to make the data partition my normal user's home directory too.  That way anything I might create, even just a little text file with some notes in or whatever, are available to both Ubuntu and Windows.

Unfortunately due to vfat/file permissions issues this doesn't quite work.  I have tried using this in /etc/fstab:

/dev/hda5    /d    vfat    uid=1000,gid=1000,iocharset=utf8,umask=000

(with user 1000's home dir set to /d) which gets me some of the way there - it works in a nongraphical terminal (Ctrl-Alt-f1, etc.) but starting an X/gnome session fails because $HOME/.drmc has the wrong permissions.

I don't really understand the umask line in /etc/fstab -- could I change that and get the permission on $HOME/.drmc to be 644?  What value would I use (I tried 644!)

If this is truly not possible, what's the best plan for making stuff available in both OSes?  Is there a solution where the shared partition is not vfat but some more Linux-friendly format that can be read in Windows or something?

Thanks in advance, Tom

---

### Post by Ampersand on 2005-12-18
It might be easiest to have a seperate home directory in /home/username, then save anything you want to copy between Windows and Linux in /d . If you use ext2 as the filesystem for the data directory, then there are programs available to make it readable in windows. I'm not sure whether it'll work better than fat32, though.

---

### Post by cotcot on 2005-12-18
I have a dual boot Breezy - XP.
I tried to do the same as you did. 
Finally it worked with following line in my fstab :

/dev/hda4       /home/nick/windows  vfat    iocharset=utf8,umask=000   0       0

The hda4 is a partition i can access from XP. I made this as a "shared" in XP. Unfortunately I do not remember exactly how i did it. I do not think this was a must to get it readable from Breezy. 
As you can see i formatted the partition to share as fat32 (because writing on NTFS is "experimental" in linux).

Regards

---

### Post by aysiu on 2005-12-18
Ubuntu's /home directory should *never* be on a FAT32 partition.

It's fine to have a FAT32 partition to share files (documents, pictures, music, etc.), but the config files and such should not live there.

Ext3 for Ubuntu (including /home).
NTFS for Windows.
FAT32 for files.

For how to mount the FAT32 partition, see the fourth link of my sig.

---

### Post by bakert on 2005-12-18
Thanks for your help guys.

I think perhaps my best solution then is to mount /d instead as /home/user/d and then use it that way?  Config files and the like will not go on my shared partition and I'll have to back them up separately but that seems like the best possible solution.

Tom

---

### Post by mikeon on 2005-12-18
Thanks for the help also, I was trying to read and write to a partion from both windows and kubuntu to share files between the two operating systems. I wanted a seperate partion, keeping my home and all other linux partitions well isolated from windows. The ubuntu faq fstab line did not seem to work whereas the solutions proposed in this thread work just fine! So, to help anyone else searching this subject, I have a fat32 partition which from winxp is the d drive. The following line in fstab allows linux to read and write to the partition:

```
/dev/hda2 /media/windata vfat iocharset=utf8,umask=000 0 0
```

---

### Post by toya on 2005-12-18
Hi, i was just about to post a same question, but luckily i searched before and found this.

I don't have that big of a hard drive so i don't want to make a fat32 partition
so my solution is that my linux keeps its file to itself, and windows to itself, and make them able to read each other's files.
I'm a new user and don't really know what to do, after going to etc/fstab
so can anyone tell me what to do after, sure i can try some stuff out since it looks pretty obvious what to put in file system, and mount point, but what i'm not sure about is the options, type, dump, and pass. 
And it seems like it is read only, so, no, i can't really try some stuff out.

for windows someone showed me a program that lets you read ext partition

So i'll really appreciate this if someone can help me.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

I think i found the solution, i went to System -> admin -> disks

---

