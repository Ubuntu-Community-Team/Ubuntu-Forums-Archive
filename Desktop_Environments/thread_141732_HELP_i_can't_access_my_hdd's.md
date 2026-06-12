---
title: "HELP i can't access my hdd's"
date: 2006-03-08
forum: Desktop Environments
---

### Post by the_real_lefty on 2006-03-08
i can only access my hdd when i am signed in as root. when i am signed in as my usual username, it tells me that i don't have permission to use them. i want to be able to access them from all users. how do i do this?

---

### Post by aysiu on 2006-03-08
Are your hard drives Windows partitions (FAT32 or NTFS)?

---

### Post by andrewsawyer on 2006-03-08
When you say you want to access your hhard disk, do you mean the data outside your home directory?  If you do, then it is set up like this for a reason.  You shouldn't have to make any changes to it.

If you are talking about a second disk that you have mounted, however it has mounted as root then you should just be able to 'chown' it.

---

### Post by aysiu on 2006-03-08
[QUOTE=andrewsawyer]
If you are talking about a second disk that you have mounted, however it has mounted as root then you should just be able to 'chown' it.[/QUOTE] Unless it's a Windows drive.

[http://www.psychocats.net/linux/mountwindows](http://www.psychocats.net/linux/mountwindows)
[http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

---

### Post by akiro.yamamoto on 2006-03-08
This is an exert of my fstab file
```

/dev/hda2       /media/data     vfat    user,umask=000        0       0
/dev/hdd1       /media/extra    ntfs    user,ro,umask=0222        0       0
/dev/hdb1       /media/old-home ext3    defaults        0       2

```
Note the type specified for each (ntfs etc.) and mount options used for each 
(user etc.) as well. 
Some of the best sources for info ?:
1) On your computer..... Click: System >> Help >> Ubuntu 5.10 Starter Guide
2) Online ..... Click the first link in my sig ;)
Anyway I hope this helps to get you started, if you need further guidance feel free
to post any errors here. Provide as much detail as possible.
Welcome to Ubuntu Linux.

---

