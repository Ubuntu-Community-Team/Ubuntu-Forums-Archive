---
title: "FAT32 permissions problems"
date: 2005-12-13
forum: General Help
---

### Post by MagisterJoe on 2005-12-13
I have a system dual-booting XP and Ubuntu.  There is a partition on my hard drive that both systems share (FAT32) for documents, etc, with each OS actually residing on their own separate partitions.  

My problem is that in Ubuntu I can only write files to this drive as root.  This becomes a real pain because I tire of opening all programs from the terminal so that I can have root permissions for saving, etc.  I went to the mount point for this drive and did the following:

joe@tweedy:/media$ ls -l
total 42
drwxr-xr-x   5 root root  8192 1969-12-31 19:00 shared

joe@tweedy:/media$ sudo chmod ugo+rwx shared

joe@tweedy:/media$ ls -l
total 42
drwxr-xr-x   5 root root  8192 1969-12-31 19:00 shared

so, as you can see, the permission changed not at all.  Nothing on the drive is read-only, as I can write to the drive in Windows without admin privileges.

Why won't my permissions change?

---

### Post by fog on 2005-12-13
Look [here]("http://tinyurl.com/b7noc")

---

### Post by frodon on 2005-12-13
Post here your fstab file if you still have problems : ```
sudo gedit /etc/fstab
```

EDIT : the fog's link should work well

---

### Post by Burke on 2005-12-13
What do you see if you `cat /etc/fstab`?

It could possibly be an option that has been specified to allow only the root user to access.

EDIT: Wow, 3 fstab posts in the space of a minute, and I was the last. I've got to learn to type quicker or refresh before I submit :)

---

### Post by MagisterJoe on 2005-12-13
Here are the relevant fstab lines (don't know the default settings...but they are probably what should be changed):

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
    /dev/hda2       /media/shared        vfat        defaults                  0           0

---

### Post by frodon on 2005-12-13
Mofify the line like that and reboot :  ```
/dev/hda2 /media/shared vfat iocharset=utf8,rw,user,umask=000 0 0
```Here are some explainations of the options if you want to understand what you do : [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by MagisterJoe on 2005-12-13
Thanks for the link.  Very informative.

---

