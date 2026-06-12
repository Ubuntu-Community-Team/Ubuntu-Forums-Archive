---
title: "[SOLVED] full / partition"
date: 2008-12-10
forum: General Help
---

### Post by jakupl on 2008-12-10
hello. I have a 7 G / partition. But suddenly it's full.
I have been removing unnecessary programs for a while, but it does not help, as all the programs for ubuntu are really small.

What can I remove that takes a lot of space? 

```
jakup@bobby:~$ cd /
jakup@bobby:/$ sudo du -s * | sort -nr | head
du: cannot access `home/jakup/.gvfs': Permission denied
du: cannot access `proc/7012/task/7012/fd/3': No such file or directory
du: cannot access `proc/7012/task/7012/fdinfo/3': No such file or directory
du: cannot access `proc/7012/fd/3': No such file or directory
du: cannot access `proc/7012/fdinfo/3': No such file or directory
20212080	home
4883884	var
1958788	usr
291616	lib
36588	boot
12188	etc
6992	sbin
5312	bin
192	root
100	dev

```

EDIT: I have done everything on [this thread]("http://ubuntuforums.org/showthread.php?t=140920") but it make little difference.

---

### Post by hyper_ch on 2008-12-10
```

df -h

```

---

### Post by drs305 on 2008-12-10
I noticed that at least the initial post didn't include checking your trash bins for trash, including the root trash bin.

Here is a link for finding and deleting all your system trash and a few other tips:
[Disk Full - Check Your Trash]("http://ubuntuforums.org/showthread.php?t=898573")

---

### Post by jakupl on 2008-12-10
```
jakup@bobby:/$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             7,0G  6,7G   36M 100% /
varrun                442M  108K  442M   1% /var/run
varlock               442M     0  442M   0% /var/lock
udev                  442M   48K  442M   1% /dev
devshm                442M   40K  442M   1% /dev/shm
lrm                   442M   39M  404M   9% /lib/modules/2.6.24-22-generic/volatile
/dev/hda3              65G   20G   42G  32% /home
overflow              1,0M   40K  984K   4% /tmp
gvfs-fuse-daemon      7,0G  6,7G   36M 100% /home/jakup/.gvfs
jakup@bobby:/$ 
```

---

### Post by logos34 on 2008-12-10
looks like /var is pretty big--most likely deb archives.  Back them up using [AptOnCD ]("http://aptoncd.sourceforge.net/")and then clear it out with apt-get clean ('autoclean' only does the partial pkgs)

> 
[https://help.ubuntu.com/community/AptGet/Howto#Maintenance%20commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance%20commands)

sudo apt-get autoclean

This command removes .deb files for packages that are no longer installed on your system. Depending on your installation habits, removing these files from /var/cache/apt/archives may regain a significant amount of diskspace.


sudo apt-get clean

The same as above, except it removes all packages from the package cache. This may not be desirable if you have a slow internet connection, since it will cause you to redownload any packages you need to install a program.

    *
      The package cache is in /var/cache/apt/archives . The command

      du -sh /var/cache/apt/archives

      will tell you how much space cached packages are consuming.

---

### Post by jakupl on 2008-12-10
I did a sudo ```
rm -v /var/cache/apt/archives/*.deb
``` a while ago, it helped a little, but my / partition is still way to full.

I would just resize the partitions, but my cd drive is currently dead, so I can't boot a gparted live cd.

---

### Post by az on 2008-12-10
Your /var folder is taking up a lot of space.  Are you running a mysql database?  There are a few applications that use up space in /var, but none of them are used in a typical desktop.

You can run

du -h /var

and take a look.


You wouldn't be in this situation if you avoided using a separate home partition...  That's why I always recommend everything on one partition - No separate home.

---

### Post by jakupl on 2008-12-10
But I find it so strange. I had Intrepid  for a long time, but a few days ago, I decided to get hardy instead. When I had Intrepid, this partition was only half full, and now short after replacing with hardy, it uses twice as much place.

I have much fewer programs installed now.

---

### Post by jakupl on 2008-12-10
It seems as though /var/archives is the sinner. It eats up 4.1 GB

Disk usage analyzer had no idea until I ran it with super user privileges.

What can I do to delete possibly unnecessary data in /var/archives?

[QUOTE="az"]Are you running a mysql database?[/QUOTE]
no... not to my knowledge. What is that?

---

### Post by jakupl on 2008-12-10
I KNOW WHAT IT IS!

Some time ago, i installed some stupid backup tool. Somehow it has made an automatic backup of my entire /home and placed it in /var/archives. hehehe.
solved.

---

### Post by drs305 on 2008-12-10
You can run the following to see if there are one or more very large files:
```
sudo find /var -size +500M
```
It is also possible you have lots of smaller files.

If you open nautilus with admin privileges you can explore your /var files and see what is taking up so much space, then delete them:
```
gksudo nautilus /var
```

---

