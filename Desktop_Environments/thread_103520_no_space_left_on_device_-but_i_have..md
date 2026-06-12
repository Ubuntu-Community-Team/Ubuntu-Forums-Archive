---
title: "no space left on device -but i have."
date: 2005-12-14
forum: Desktop Environments
---

### Post by dartakaum on 2005-12-14
I copied some files to my hard drive till it gets full, no problem then.

I run gnome-system-manager and it says i got 1gb free.

Everytime i try to run any application it just says i have no space, so it can write temp files.

even with nano, if i try to write a file text it won't write it.

i erased some files, (about 1gb) and it stills says the same thing.

what could be?

---

### Post by prammy on 2005-12-14
how much space do you have left in /tmp ?

---

### Post by dartakaum on 2005-12-15
well, i resolve it, by deleting more files... :\

i dunno is why OS needs about 2gb...

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              44G   41G  297M 100% /
tmpfs                 252M     0  252M   0% /dev/shm
tmpfs                 252M   13M  240M   5% /lib/modules/2.6.12-9-686/volatil

```

---

### Post by az on 2005-12-15
[QUOTE=dartakaum]well, i resolve it, by deleting more files... :\

i dunno is way OS needs about 2gb...
[/code][/QUOTE]

5 percent of the disk space is allocated to root so that kernel daemons can keep running if you run out of space.  Otherwise the system would crash. 

Also, ext3 can get quite fragmented when you use up most of the disk space, like that.

---

### Post by dartakaum on 2005-12-15
is there a way to defragment?

---

### Post by psusi on 2005-12-15
[QUOTE=dartakaum]is there a way to defragment?[/QUOTE]

Unfortunately, no.  The Linux community has long felt ( wrongly ) that defragmenting is not required because Linux filesystems are immune to it ( they are not ).  

The only thing you can do is backup all your files ( i.e. with tar ), format the partition, then restore.

I wouldn't worry about it too much though because Linux filesystem drivers do a good job of minimizing fragmentation, as long as there is still some free space to play with.

---

### Post by az on 2005-12-16
[QUOTE=dartakaum]is there a way to defragment?[/QUOTE]
Free up some disk space.

---

### Post by megamania on 2005-12-16
[QUOTE=azz]5 percent of the disk space is allocated to root so that kernel daemons can keep running if you run out of space.  Otherwise the system would crash. 
[/QUOTE]

Dartakaum, on this regard you may want to check this out:

[http://ubuntuforums.org/showthread.php?t=78333](http://ubuntuforums.org/showthread.php?t=78333)

---

### Post by psusi on 2005-12-16
I would not recomend doing that.  

If you set the reserved space to zero, and you do use up all the space on the disk, the computer might not boot up any more.  

Also the more full the volume gets, the more fragmented it is going to get, and you don't want that.  

If your disk is 95% full, then yea, you need to get a bigger disk.  Or start compressing some stuff.  Or burn some data to cds or something and get it off the hard drive.

---

### Post by dartakaum on 2005-12-16
thanks for all the replies, i will free some space! :\

---

### Post by a50sn95 on 2005-12-16
You looked in .Trash ? There may be some stuff in there....

---

