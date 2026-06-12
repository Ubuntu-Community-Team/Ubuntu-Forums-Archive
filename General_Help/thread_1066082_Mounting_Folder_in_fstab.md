---
title: "Mounting Folder in fstab"
date: 2009-02-10
forum: General Help
---

### Post by tamer_radi on 2009-02-10
Hi,
I am trying to mount Folders not partitions nor devices  , (*soft mount I think*)
like ( **mount --bind folder1 folder2**)

But I want this to be mounted automatically , ( via fstab )
When I add 
/media/disk/folder /home/user/folder ntfs-3g defaults,locale=en_US.UTF-8 0 0
I get error about mounting directory

This is the first problem 
( Please tell me the correct syntax for mounting directories in fstab)


The Second thing , I've ran into this command while searching
"**mount -p > /etc/fstab**"
seems to write the correct syntax of the current mount to fstab
seems great , but doesn't work in ubuntu !
I don't know why "mount -p" command in Ubuntu does different thing 
So what is command that does print the syntax of fstab in Ubuntu ?


notes : 
I am using Ubutnu 8.04
Folder I want to mount in ntfs partition
I've installed ntfs-3g
I am a beginner :)


Thank you in advance

---

### Post by adder1972 on 2009-02-10
Hi,

You need to use the "bind" command.

Check out my blog-entry here:  [http://arcticlinux.blogspot.com/2007/08/mounting.html](http://arcticlinux.blogspot.com/2007/08/mounting.html)

---

