---
title: "Full Harddisk!"
date: 2006-08-08
forum: Desktop Environments
---

### Post by Flavian on 2006-08-08
Hi guys, I got a little problem.
My Ubuntu Root filesystem is 8 GB big and a bunch of days ago I did this howto.
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)
Thinking I can backup my system.
It did not work how I wanted, so I aborted the process, by simply closing the console.
But since then when I start up it says that my Disk is 97% full!
I KNOW that there was MUCH MORE space before I did the howto.

I can't find the files though that might cause the problem.
Can it be that there are some files left over on the system, because I aborted the process?

I would be so greatful for any advice and help!
This is really annoying to me :(

Thanks in advance
Flo

---

### Post by halfvolle melk on 2006-08-08
> **Flavian said:**
> Can it be that there are some files left over on the system, because I aborted the process?
Dunno what caused it, but an easy way of finding out what's clogging up the HD is to run this:
```
cd /
sudo du | sort -n
```

---

### Post by clint1010 on 2006-08-08
There may have been a file created during the backup process you folowed, don't know what might have happened if you stopped it mid way. Do you remember the name of the backup file you were creating? "backup.tgz"? browse the root directory and remove this file if it is created. This file may well be quite large.

sudo nautilus

you can do a search in nautilus to locate the file if you know what it might be called. Traditionally there are very few files located at the root of the file system, (plenty of folders though), should be easy to locate the file.

good luck

---

### Post by etank on 2006-08-08
If you want a graphical way to see what is taking up space on your system try installing baobab or filelight. Both of these do a really good job.

---

### Post by Flavian on 2006-08-08
I tried baobab, but everything seems to be in order, I can't find the files.
The bigest folder is /usr is that normal?

I would be greatful if someone could tell me if there can be some temporary files left on the system!

Thanks
Flo

---

### Post by Flavian on 2006-08-08
Ok, THIS is WEIRD!
I made a screenshot so you guys can see what's going on.
As I said, I made a backup of my files 2 days ago, I aborted the process and now my HDD is nearly full.

I just became aware of the fact that there is something very wrong!
Baobab says:

Total file system capacity. 8.7 GB (used 7.5 available 1.2 GB)
BUT the scan shows 
**for /**
**4.6 GB used** = 100%

There must be some data elsewhere but in root /
But where?! *lol*
Correct me if I missinterpreted what Baobab told me, but that would also explain why I could create a 2.5 GB tar.bz2 file 2 days ago. The funny thing is though that I already deleted it.
The space seems to be in use though...

I would appreciate any help!
Thanks
Flo

---

### Post by Flavian on 2006-08-08
*lol* sorry for spaming my own topic, but right after I posted the last post I found the "bug".
I am not quiet sure how that happened, for that I am too much of a beginner, BUT I did the following:
```

sudo umount -a
sudo du | sort -n > /home/florian/dateien.txt

```

I unmounted all drives and than wrote a file listing to a txt file.
There it gave me the following information:
3579188	./root/.Trash
right AFTER ./usr
which means it is BIGGER than ./usr
that caught my attention.

Finally found out that the two packed backup files where still in the trash folder, EVEN THOUGH they were NOT in the trash!
So I manually deleted the content of the folder and now I got 3 GB of extra free space :)

Thanks to everyone who offered his help.
Flo

---

