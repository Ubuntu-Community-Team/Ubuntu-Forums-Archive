---
title: "Can not acess hard drive"
date: 2006-10-01
forum: Desktop Environments
---

### Post by kevindubrow on 2006-10-01
Hi, I have put a second hardrive as a slave into my computer so I would have some space now that I have partitioned my master hard drive in half, but can not access it with Ubuntu. I know it is probably because this is a hard drive formatted for Windows 98, but I don't want to format it because it has too many files to be able to backup. Is there a way to access this drive without deleting all of the media on it? Thanks.

---

### Post by sarhento_lobo on 2006-10-01
Did you go through the process of mounting it? Refer to: [https://help.ubuntu.com/community/MountingWindowsPartitions]("https://help.ubuntu.com/community/MountingWindowsPartitions")

Scroll down to the section named "Accessing the Files on Your Windows Partition From Ubuntu.:

---

### Post by kevindubrow on 2006-10-01
Umm, I'm new to Linux and its alittle technical.

When it says, " create a folder where the partition will be accessed. mkdir /media/windows" Whad is the mkdir part of that? is that just the name of that persons hard drive? Thanks.

---

### Post by sarhento_lobo on 2006-10-01
"mkdir" is a command you enter into a console. This command executes the creation of a directory in the file system. In the case of "mkdir /media/windows", this means you're creating a folder/directory (they're the same thing, "directory" is the older term), in the "media" directory, which itself is in the root directory (denoted by "/"). 

To bring up a console, go to Applications > Accessories > Terminal. Make sure to type in each line exactly as specified in the wiki, then end the line with an <enter> keypress. Pressing <enter> executes the command(s).

---

### Post by kevindubrow on 2006-10-03
Ok, well when I typed this in I get a message saying "can not read windows, permission denied". What should I do about that?

---

### Post by CatKiller on 2006-10-04
[http://psychocats.net/ubuntu/permissions](http://psychocats.net/ubuntu/permissions)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by kevindubrow on 2006-10-05
Hi, I'm at the fstab file using the graphical option, but do not know what to edit in this folder. I looked at the links, but don't see anything about what I actually have to edit to access the hard drive (I believe I am trying to access /dev/hdb)

---

### Post by kevindubrow on 2006-10-05
Idea...am I supposed to type in a completly new harddrive on this list?

---

### Post by CatKiller on 2006-10-05
> **kevindubrow said:**
> Hi, I'm at the fstab file using the graphical option, but do not know what to edit in this folder. I looked at the links, but don't see anything about what I actually have to edit to access the hard drive (I believe I am trying to access /dev/hdb)

You start by making a directory somewhere. Where you make it, and what you call it, are entirely up to you, and depend on what it will be used for, and what will be in it. Most guides suggest that it should be either in /media, if you want it to be displayed as an icon on the desktop, or /mnt, if you don't. Both of these are tidy places to put it, but you could put it anywhere that you want. This is the "mount point", and when the partition is mounted, the contents of that partition will be displayed in this directory.

If you make this directory somewhere other than your Home folder, you'll probably need root permissions to make the directory. The pages on permissions you've already read will show you why this is, and why it is good to use the **sudo** command when you have to. So, assuming you wanted to make a directory called "data" in /mnt as your mount point, you would use the command```
sudo mkdir /mnt/data
```You will be asked for your password (the one you used to log in with), and this will not be displayed as you type it.

/etc/fstab is the **f**ile**s**ystem **tab**le, and is the map of how the drives in the computer correspond to places in the filesystem. [This post]("http://www.ubuntuforums.org/showpost.php?p=1557220&postcount=10") may explain a bit about what's going on. Or it might not - it is one of mine, after all. You'll need root permissions to edit this file, too, so the command is ```
gksudo gedit /etc/fstab
```

What you add to this file depends on a number of things; most particularly which device it is, where you want it to be mounted, what filesystem the partition has on it, and which permissions you'd like users to have on the data in the partition. 

Hard drive devices are named hdx or sdx depending on whether the drive is IDE/PATA (h) or SCSI/SATA (s), and the x is a, b, c, d, and so on, depending on whether the drive is the first, second, third, fourth, and so on, in the computer. Partitions on a particular drive are named (h|s)dxn, where the n is 1, 2, 3, and so on. Which partition you want depends on what type it is - you can have up to four Primary partitions, or any number of Logical drives in an Extended partition. So you might have hdb1 and hdb5, say, with data in. The command **sudo fdisk -l** will give you a list of the partitions that you have, and hopefully the size and filesystem used will enable you to identify the partition that you wish to mount. **man mount** and **man fdisk** may give you some more information.

With the background out of the way, you may find these links useful:

[ How to mount Windows partitions (FAT) on boot-up, and allow all users to read/write]("http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite")
[AutomaticallyMountPartitions]("https://help.ubuntu.com/community/AutomaticallyMountPartitions#head-80128df9c1c4215d74e3f016b5cd2c2352da247c")
[Mounting Windows Partitions in Ubuntu]("http://www.psychocats.net/ubuntu/mountwindows")

---

### Post by kevindubrow on 2006-10-05
Ok, I am now able to view the hard drive from going to the filesystem, media, windows. This is great, but I thought I was setting it up to beable to view from my folder that was made for my user. The user name is stephen, so would I have to do mkdir /stephen to mount it there? Thanks.

---

### Post by kevindubrow on 2006-10-05
Ok, nevermind I think I have it. Thanks a lot!

---

### Post by CatKiller on 2006-10-05
If you would really like to mount the partition in your own Home folder, then yes, you would need to make a directory there and use that directory as your mount point in /etc/fstab. Or you could run ```
gconf-editor
``` and navigate to apps/nautilus/desktop and check the volumes_visible box to get an icon for it on the Desktop from where it is already, or you could use ```
ln -s /media/windows windows
``` to have an icon on the Desktop **and** access it as a subdirectory of your Home folder.

EDIT: No worries. Glad you've got it now.

---

### Post by juttybean on 2006-10-05
none of this information helps me because i dual booted.  is there any way to mount a windows partition which is a separate hard drive that is a boot device?

---

### Post by CatKiller on 2006-10-05
> **juttybean said:**
> none of this information helps me because i dual booted.  is there any way to mount a windows partition which is a separate hard drive that is a boot device?

Yes. Unless you're physically disconnecting it from the computer each time, in which case witchcraft is the only solution.

Read the links. It's all the same method whether the partition you want to mount is on the same hard drive as your root partition or not. It doesn't even have to be in the same **computer**.

---

