---
title: "Computer always busy?"
date: 2008-12-15
forum: General Help
---

### Post by Castlef on 2008-12-15
I have a question... I assume that any noise besides fan in your computer is from the hard drive correct? In ram there is no moving part... in the CPU there is no moving part... so the constant "working" sound my computer is making is the hard drive being written to.

My question is what in the world is writing to my hard drive CONSTANTLY forever and ever. it never stops. It never ceases . Why oh why? I do not have any background tasks like some file sharing program going on. I almost have a default base install .  So why is it doing this? I don't want it to. In windows vista at least it stops "working" and there are periods when it is silent... especially when I am not doing an operation that requires the use of the hard drive... and since I have 4 gigs of ram that should be rare indeed.

So how do I figure out exactly what is going on in my computer? what is writing to the hard drive? Is it tracker or something?

---

### Post by HermanAB on 2008-12-15
Syslog is always writing to the hard disk.  If the system is working properly, you can stop syslog with no ill effect.  It is a good idea to stop it on a Laptop machine to conserve battery.

You can see what else is going on with 'top', 'htop' and 'ntop'.

Cheers,

Herman

---

### Post by Arup on 2008-12-15
Disk I/O in Linux is way less than in Windows however you can make it minimal by reducing tracker resources. To see disk I/O install GkrellM and you will get to see disk activity graphically.

---

### Post by sdennie on 2008-12-15
You can figure out what is causing the disk activity with:

```

sudo sh -c "echo 1 > /proc/sys/vm/block_dump"
tail -f /var/log/syslog

```

To turn that log spam off use:

```

sudo sh -c "echo 0 > /proc/sys/vm/block_dump"

```

My guess is you are just seeing the ext3 journal commit and dirty writebacks (both set to happen every 5 seconds).  If you want to change that behavior, see this guide (but, read the warnings carefully): [  HOWTO: Decrease disk activity]("http://ubuntuforums.org/showthread.php?t=839998")

---

