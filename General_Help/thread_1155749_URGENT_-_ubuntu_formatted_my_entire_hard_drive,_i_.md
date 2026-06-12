---
title: "URGENT - ubuntu formatted my entire hard drive, i need to recover"
date: 2009-05-11
forum: General Help
---

### Post by krikesa on 2009-05-11
Here is my problem. 
I tried to install ubuntu on my C: partition of hard drive. I had 2 partitions on that hard. Now, ubuntu formatted my both partitions, and now it is entire disc in one partition. On D partition I had many important documents and data. Is there any way to recover that data. Please, help me it is very urgent for me, becouse I need my computer. 

Also, before I had windows, and partitions were NTFS.

---

### Post by logos34 on 2009-05-11
On the ubuntu live cd session go to panel>System>admin>synaptic pkg mgr>settings>repos>enable **Universe** repository

then reload and install **Testdisk**.

to start app run in a terminal:

> sudo testdisk

read this documentation:

[http://www.cgsecurity.org/wiki/Data_Recovery_Examples#Recovery_of_reformated_partition](http://www.cgsecurity.org/wiki/Data_Recovery_Examples#Recovery_of_reformated_partition)
[http://www.users.bigpond.net.au/hermanzone/p21.html](http://www.users.bigpond.net.au/hermanzone/p21.html)
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by krikesa on 2009-05-11
I can not install Testdisk :(

---

### Post by Peter09 on 2009-05-11
Do Not use your machines Hard Drive - you will lose more data. As said above you must use a LiveCD as this does not write to the hard drive.

---

### Post by Peter09 on 2009-05-11
note that in Linux case matters - Testdisk and testdisk are not the same thing. Make sure you enter the correct command.

---

### Post by bobince on 2009-05-11
Has worked for me in the past: [http://www.partition-recovery.com/](http://www.partition-recovery.com/)

---

### Post by kellemes on 2009-05-11
> **krikesa said:**
> Here is my problem. 
I tried to install ubuntu on my C: partition of hard drive. I had 2 partitions on that hard. Now, ubuntu formatted my both partitions, and now it is entire disc in one partition. On D partition I had many important documents and data. Is there any way to recover that data. Please, help me it is very urgent for me, becouse I need my computer. 

Also, before I had windows, and partitions were NTFS.

As said by others, every second you continue to use your current install of Ubuntu, you will loose more data.
So use a live-system to find, choose and use your way of recovery.

Also, before installing an os you should expect trouble, and so backing-up your data on an external device is highly recommended to say the least.
But I'm sure you know that by now ;-)

Good luck.

---

### Post by scottuss on 2009-05-11
I'm going to be a complete moron here and very unhelpfully suggest that next time you have backups, and read what the installer says before clicking next. Ubuntu didn't get rid of your data, you did.

That's not meant to sound horrible, it's just to highlight the fact that backups are sooooo important! (I learnt the hard way too mate :( )

---

### Post by krikesa on 2009-05-12
> **scottuss said:**
> I'm going to be a complete moron here and very unhelpfully suggest that next time you have backups, and read what the installer says before clicking next. Ubuntu didn't get rid of your data, you did.

That's not meant to sound horrible, it's just to highlight the fact that backups are sooooo important! (I learnt the hard way too mate :( )

Thanks all you guys. Problem solved.

I know it all that you said, but s**t happens sometimes ;)

---

