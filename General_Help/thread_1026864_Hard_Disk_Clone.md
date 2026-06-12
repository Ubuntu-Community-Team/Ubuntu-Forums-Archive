---
title: "Hard Disk Clone"
date: 2008-12-31
forum: General Help
---

### Post by RedSingularity on 2008-12-31
Hey guys, i was wondering what i can do to keep a backup of my Hard disk in case i have a system failure.  I want to be able to put the copied Hard disk info onto the new drive.  I heard about creating an ISO image of my HDD.  Or a clone?  What can i do to get a ISO image of it for safe keeping?

---

### Post by jerome1232 on 2008-12-31
You can use dd, it's installed by default.

There's also [Partimage]("http://www.partimage.org/Main_Page"), It's in the repos.

PING - **P**artimage **I**s **N**ot **G**host [http://ping.windowsdream.com/]("http://ping.windowsdream.com/") is a live cd distro for this type of thing.

---

### Post by logos34 on 2008-12-31
I use Partimage to backup my /, then burn it to dvd.  (I have a separate /home which I backup with tar).

---

### Post by RedSingularity on 2008-12-31
Ok i got it.  Now is there any manual or guide i can follow to use Partimage?  I would like to back up my / and my /home as well and probably burn them to DVD like logos.

---

### Post by 2hot6ft2 on 2008-12-31
Another option from another thread.
> Clonezilla, fastest ever cloning i have ever done is using CLONEZILLA(indeed it is top notch app).

i have cloned several HDD and networked machines with it, locally and on network with no problem what so ever. Great app for one off complete system state clone/backup

Last week I cloned my laptop's HDD 120GB locally within 35 mins.

[http://clonezilla.sourceforge.net/](http://clonezilla.sourceforge.net/)

---

### Post by albinootje on 2008-12-31
> **2hot6ft2 said:**
> Another option from another thread.

+1 
I like Clonezilla too. I find the Ping website confusing, but I've happily used Clonezilla several times now (Even inside VirtualBox!).

---

### Post by drs305 on 2008-12-31
> **Shadow121 said:**
> Ok i got it.  Now is there any manual or guide i can follow to use Partimage?  I would like to back up my / and my /home as well and probably burn them to DVD like logos.

I use partimage. It doesn't copy empty space and my backups of a fairly basic install without data files run about 1.9-2.5GB compressed. Since you asked for a guide:
[http://www.psychocats.net/ubuntu/partimage]("http://www.psychocats.net/ubuntu/partimage")

---

### Post by logos34 on 2008-12-31
> **Shadow121 said:**
> ONow is there any manual or guide i can follow to use Partimage?  I would like to back up my / and my /home as well and probably burn them to DVD like logos.

The official docs are not a lot of help, that's for sure.

This one is fairly decent:

[http://www.debianadmin.com/backup-and-restore-linux-partitions-using-partimage.html](http://www.debianadmin.com/backup-and-restore-linux-partitions-using-partimage.html)

---

### Post by RedSingularity on 2008-12-31
Ahhh thats perfect!  Thanks a lot guys!!!

---

