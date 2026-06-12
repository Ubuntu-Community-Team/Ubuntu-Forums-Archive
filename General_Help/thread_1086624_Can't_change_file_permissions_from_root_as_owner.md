---
title: "Can't change file permissions from root as owner"
date: 2009-03-04
forum: General Help
---

### Post by glubbdrubb on 2009-03-04
[warning: if this question has been asked before please just forward me onto it. I rarely find what I need using the search tool. And if this thread is in the wrong place I am sure a moderator will move it. Thanks]

A while ago I copied my Home Directory to a removable HDD as a temporary back-up solution. I have since found out that I have lost all ownership of the file to root. I logged on as root (I don't know how to do this in the terminal) and tried to change the the ownership and group permission settings back to my user name but it would keep flipping back to root.

I am stuck now because I want to compress and archive the folder for history's sake but can't because I am not root. (and no, I don't want to do it as root)

Please help

---

### Post by cdenley on 2009-03-04
What filesystem is on the removable hard drive? FAT32 and NTFS cannot store unix permissions.

---

### Post by bodhi.zazen on 2009-03-04
> **glubbdrubb said:**
> [warning: if this question has been asked before please just forward me onto it. I rarely find what I need using the search tool. And if this thread is in the wrong place I am sure a moderator will move it. Thanks]

A while ago I copied my Home Directory to a removable HDD as a temporary back-up solution. I have since found out that I have lost all ownership of the file to root. I logged on as root (I don't know how to do this in the terminal) and tried to change the the ownership and group permission settings back to my user name but it would keep flipping back to root.

I am stuck now because I want to compress and archive the folder for history's sake but can't because I am not root. (and no, I don't want to do it as root)

Please help

moved to general help.

As indicated by cdenley my guess would be you copied the files to a FAT or NTFS file system.

It would help if you posted the exact commands you are running and any error messages you are getting.

---

### Post by glubbdrubb on 2009-03-04
Yes, it is formatted with NTFS. (which is how most of these consumer drives ship. And I need it to stay that way because I need other PC's to read it)

I did not use any commands to copy or compress the folder. I logged in as root using the GUI (I don't know the commands to do it any other way). 

The error was:

An error occurred while adding files to the archive.
Permission denied


So how can I access and change the files stored on the drive if ntfs does not support permissions?

What is cdenley?

---

### Post by cdenley on 2009-03-04
> **glubbdrubb said:**
> I did not use any commands to copy or compress the folder. I logged in as root using the GUI (I don't know the commands to do it any other way).

Logging in to the GUI as root is a terribly insecure thing to do.

> **glubbdrubb said:**
> 
So how can I access and change the files stored on the drive if ntfs does not support permissions?

You can either change the user you access the files as, or change the way it is mounted to assign it the correct permissions at mount time.

> **glubbdrubb said:**
> 
What is cdenley?
I am.

---

### Post by bodhi.zazen on 2009-03-04
See this guide for how to set permissions : 

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by glubbdrubb on 2009-03-05
Thanks for your help so far. 

I read through the fstab page but me in my inexperience did not see the part where drive permissions are explained. Please help.

I do understand the power and danger of root(I have administered XP for 5 years and Admin + average user = trouble). But I have two issues. I don't know the commands to do what I need to do in the terminal and when I do log in as root it is only for very specific functions (like changing file permissions).

---

### Post by cdenley on 2009-03-05
> **glubbdrubb said:**
> Thanks for your help so far. 

I read through the fstab page but me in my inexperience did not see the part where drive permissions are explained. Please help.

I do understand the power and danger of root(I have administered XP for 5 years and Admin + average user = trouble). But I have two issues. I don't know the commands to do what I need to do in the terminal and when I do log in as root it is only for very specific functions (like changing file permissions).
This seems pretty relevant:
> 
VFAT/NTFS:

Ownership and permissios of vfat / ntfs are set at the time of mounting.


Also, running nautilus as root is much safer than running everything as root.
```

gksu nautilus

```

---

### Post by bodhi.zazen on 2009-03-05
The basic format is

mount /dev/sdxy /mount_point -o uid=1000,gid=100,umask=007

uid = user 
gid = group
umask = set permissions

The "tick" is umask if the inverse of permissions , or permissions not to have.

See this link, umask is at the bottom

[http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html)

---

