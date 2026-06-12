---
title: "Filecount and directorysize in Ubuntu not the same as in XP and FreeNAS"
date: 2009-04-01
forum: Desktop Environments
---

### Post by Cupster on 2009-04-01
Hi everyone,

another greenie here :)

I managed to get a lot of issues I had solved by searching but this one is just freaking me out :)

I have 1 harddisk in my PC which has partitions for booting Ubuntu and XP and also a datapartition (NTFS) which is accessible from both
the end goal is to kick XP out of the picture but first I need to make sure my backups are working

now when I right-click the directory I want to backup in XP (on NTFS partition) it tells me the following
```

58.269 files 3.401 folders
61,9GB
62,0GB size on disk
```

when I right-click in Ubuntu on that same directory (on NTFS partition) in Nautilus it tells me
```
107,927 items, totalling 74.0 GB
```

this part I already don't understand..

now when I use a terminal to get the number of files
```
ls -Rl folder/ | wc -l

```
I get as result
```
128941

```

so yet another number..

I use Rsync to copy the files over to my FreeNAS backup server
```
rsync -e ssh -avh --delete --stats /media/disk/backupfolder/ root@192.168.1.250:/mnt/SecureDisk/rsync/backupfolder/ >> $LOGFILE_RUN 2>&1;STATUS="$?"
```
after completion, I find the following in the log file
```
Number of files: 108397
Number of files transferred: 0
Total file size: 79.49G bytes
```
again the numbers don't match

when I now open Putty to ssh to FreeNAS and run the same command as in the terminal there
```
ls -Rl folder/ | wc -l

```
I get as result
```
129680

```

and when I browse to the directory with Nautilus by Samba and right-click to get the properties, I get
```
81,478 items, totalling 50.7 GB
(some contents unreadable)
```
no idea why this is also different and why I get "contents unreadable"

sorry for the overflow of info but I've tried all sorts of things up to the point I don't know what I'm doing anymore :)
I hope someone can explain what is happening.
thanks a heap in advance

---

### Post by Cupster on 2009-04-03
*bump*

hope it's not to early to do this :)
thread was already way down

I'm really freaking out here
would just like to make sure my backups are ok and I can keep running them in Linux
but to do this I need to know how to verify

---

