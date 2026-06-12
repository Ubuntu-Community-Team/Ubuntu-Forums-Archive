---
title: "Truecrypt permission problem"
date: 2009-06-21
forum: Desktop Environments
---

### Post by yankee83 on 2009-06-21
Hi,

I made this post already [on the truecrypt.org forums]("http://forums.truecrypt.org/viewtopic.php?p=69676") but I think that I will reach more people here. Sorry for crossposting.

I am using truecrypt 6.2a on Ubuntu 9.04 to encrypt my home partition. Because I wanted to use ext4, I followed this tutorial:
[http://www.configblog.com/2009/06/truecrypt-and-ext4/](http://www.configblog.com/2009/06/truecrypt-and-ext4/)

During the process, I copied my original home dir files to the outer volume and afterwards also to the hidden volume. In theory, the content of both volumes should have been the same, in particular file permissions and ownership.

Kdm was changed to invoke truecrypt (truecrypt /dev/sda6 /home), to ask for the password and mount the partition to /home before showing the user login prompt. This process works very well with the hidden volume but when I opt for mounting the outer volume, file permissions seem to be messed up and kde is not able to access the home dir.

All files and folders are assigned permission 700, including the home dir itself. All files are owned by my everyday user, again including the home dir itself, which should be owned by root instead.

If I use chmod or chown on the files (even as root), nothing happens. I also tried to copy over the files to the outer volume again but that does not change anything. I can add umask and uid to the mount command but I don't want to have unified file rights but exactly those of the original files. In particular, /home itself should be owned by root while all subfolders should be owned by their respective users. As the hidden volume does not show any such problems, I assume that it should also be possible with the outer volume.

Do you have any idea what I am doing wrong here?

Thank you very much for your help.

---

### Post by yankee83 on 2009-06-23
The problem is that the "none" filesystem of truecrypt --whichever that is-- does not support unix file permissions, neither does FAT.
I tried reiserfs and various extY but they are destroyed once I create the hidden partition.

Does anyone know any filesystem that is robust to the creation of a hidden volume AND supports unix file permissions?

---

### Post by yankee83 on 2009-06-27
Anyone?

---

