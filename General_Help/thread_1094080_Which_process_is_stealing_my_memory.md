---
title: "Which process is stealing my memory?"
date: 2009-03-12
forum: General Help
---

### Post by azzid on 2009-03-12
Hi,

I am starting to feel quite frustraded here, I have a Ubuntu 7.04 which is allocating all its memory. Since the machine is virtual the virtual host is wining about the memory beeing fully allocated all the time.

I have been unable to spot anything beeing wrong with the machine, but even if it still does what it's supposed to I'd like to find the source of the issue.

I though that would be easy, just some magic 'ps | grep' stuff and the process hogging all the memory would appear. I have however been unable to locate such a command.

Google gives me nothing, 'man ps' gives me nothing.

Commands like 'free' show that all but 20mb of the servers memory is allocated, but I just cant seem to figure out which process is hogging the memory.

This must be something really easy that I am just doing wrong. 

Please help me find out where my memory is going!

---

### Post by pennacook on 2009-03-12
You could use 'top' to locate memory usage. Hit "M" after initial display to sort by memory use.

---

### Post by azzid on 2009-03-12
Thanks for the suggestion!

Already been there though. =/

It looks like this (with the 'M' sort):
```
top - 17:15:05 up 29 days,  7:40,  1 user,  load average: 0.01, 0.03, 0.21
Tasks:  55 total,   2 running,  53 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    515956k total,   510144k used,     5812k free,    19584k buffers
Swap:   489940k total,      120k used,   489820k free,   425324k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
19292 root      15   0  8032 2484 2020 R  0.0  0.5   0:00.05 sshd
    1 root      18   0  2912 1848  524 S  0.0  0.4   0:01.43 init
19294 root      15   0  4108 1836 1400 S  0.0  0.4   0:00.02 bash
 3777 klog      18   0  2556 1376  400 S  0.0  0.3   0:00.05 klogd
19307 root      15   0  2320 1132  888 R  0.0  0.2   0:00.05 top
 3946 root      15   0  5084  968  640 S  0.0  0.2   0:02.68 sshd
 4005 root      18   0  2280  788  632 S  0.0  0.2   0:00.06 cron
 3970 statd     18   0  1840  744  640 S  0.0  0.1   0:00.01 rpc.statd
 3863 root      15   0  2040  664  540 S  0.0  0.1   0:21.01 vmware-guestd
 2338 root      17  -4  2296  624  376 S  0.0  0.1   0:00.18 udevd
 3757 root      18   0  1700  600  492 S  0.0  0.1   0:00.40 syslogd
 3980 root      15   0  3648  592  344 S  0.0  0.1   0:00.01 rpc.idmapd
 3775 root      18   0  1796  528  432 S  0.0  0.1   0:00.04 dd
 3722 root      18   0  1652  512  440 S  0.0  0.1   0:00.00 getty
 3723 root      18   0  1652  512  440 S  0.0  0.1   0:00.00 getty
 3726 root      18   0  1652  512  440 S  0.0  0.1   0:00.00 getty
 3727 root      18   0  1648  508  440 S  0.0  0.1   0:00.00 getty
 3728 root      18   0  1652  508  440 S  0.0  0.1   0:00.00 getty
 3731 root      18   0  1648  504  440 S  0.0  0.1   0:00.00 getty
 3994 daemon    15   0  1908  420  300 S  0.0  0.1   0:00.00 atd
 3929 root      25   0  2568  396  176 S  0.0  0.1   0:00.00 rpc.mountd
 3515 daemon    15   0  1764  380  288 S  0.0  0.1   0:00.01 portmap
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0

[the rest all got 0% memory allocation]

```

As you can see the process memory allocation can in no way be held accountable for the total memory being allocated.

Still feeling like a retard here, what am I missing?

---

### Post by KayakJim on 2009-03-12
What is the output of "free"?

---

### Post by azzid on 2009-03-12
```
root@ubuntu704:~# free -m
             total       used       free     shared    buffers     cached
Mem:           503        494          9          0         19        412
-/+ buffers/cache:         62        441
Swap:          478          0        478

```

---

### Post by KayakJim on 2009-03-12
Your system does not have a lot of total memory to start with but it still has a lot free.

The linux kernel likes to takes as much memory as possible to have it on hand. This can be seen by the first line (Mem) where out of a total of 503 the system has reserved 494 leaving 9 free.

The key numbers to look at are on the second line (buffers/cache) where only 62 are actually used and 441 are still free.

Does the above help make sense of things?

---

### Post by Slim Odds on 2009-03-12
Install htop, it does a nice job of showing more detail in memory usage (via colors).

There is a ton of confusion about how linux uses memory. You might want to do some research on the subject.

Bottom line, linux will use your memory for something. Unused memory is **not** a good thing.

---

### Post by MaxIBoy on 2009-03-12
Yeah, the more memory you can put to use, the better. Ideally, you can load some of your commonly-used programs/files into RAM to reduce hard drive wear and tear, and to make sure things are as snappy and responsive as possible.

Incidentally, why are you still using Feisty? That's not supported anymore, not that I know of.

---

### Post by azzid on 2009-03-12
> **KayakJim said:**
> Your system does not have a lot of total memory to start with but it still has a lot free.
This machine is only running nfs, nothing else. Since I can run Nagios on a similar machine with 32 mb of ram with no error from the vHost I think this should work to ;)
> **KayakJim said:**
> The linux kernel likes to takes as much memory as possible to have it on hand. This can be seen by the first line (Mem) where out of a total of 503 the system has reserved 494 leaving 9 free.
The key numbers to look at are on the second line (buffers/cache) where only 62 are actually used and 441 are still free.
Oh, great to hear! But where is the memory going? Why doesn't it show up in top?
> **KayakJim said:**
> Does the above help make sense of things?
Sure helps alot, but I'd really like to delve deeper into this subject, you got a good source for me to learn more from?

> **Slim Odds said:**
> Bottom line, linux will use your memory for something. Unused memory is **not** a good thing.
I am aware of this, I'm just trying to understand what happens to the memory, my other machines doesn't cause the vHost to scream...

> **MaxIBoy said:**
> Incidentally, why are you still using Feisty? That's not supported anymore, not that I know of.
Well, no other reason than me beeing to lazy to upgrade. ;) I don't really know how to do it either, last time I used a upgrade script it destroyed the server...

---

### Post by KayakJim on 2009-03-12
> **azzid said:**
> Sure helps alot, but I'd really like to delve deeper into this subject, you got a good source for me to learn more from?

Here are just a couple of links that I quickly found that might help you out.

[http://virtualthreads.blogspot.com/2006/02/understanding-memory-usage-on-linux.html]("http://virtualthreads.blogspot.com/2006/02/understanding-memory-usage-on-linux.html")

[http://www.mydigitallife.info/2007/09/24/how-to-check-memory-usage-in-linux-based-server/]("http://www.mydigitallife.info/2007/09/24/how-to-check-memory-usage-in-linux-based-server/")

A Google search for "Linux memory usage" or some variation should produce additional information.

---

### Post by Slim Odds on 2009-03-12
> **azzid said:**
> I am aware of this, I'm just trying to understand what happens to the memory, my other machines doesn't cause the vHost to scream...

Did you try htop?

It shows the memory breakdown of used/buffers/cache

---

### Post by MaxIBoy on 2009-03-12
> **azzid said:**
> Well, no other reason than me beeing to lazy to upgrade. ;) I don't really know how to do it either, last time I used a upgrade script it destroyed the server...At the very least, re-enable the repositories that got moved to different hosts.
[http://ubuntuforums.org/showpost.php?p=6319924&postcount=4](http://ubuntuforums.org/showpost.php?p=6319924&postcount=4)

---

### Post by azzid on 2009-03-13
> **Slim Odds said:**
> Did you try htop?
Tried it just now, very pretty tool, I'll add it to my list of favorites. ;)

It is only reporting 102/503MB memory usage, which is more sensible.

Thanks for the tip!

> **MaxIBoy said:**
> At the very least, re-enable the repositories that got moved to different hosts.
[http://ubuntuforums.org/showpost.php?p=6319924&postcount=4](http://ubuntuforums.org/showpost.php?p=6319924&postcount=4)

Did that, there where no updates, but I think it helped alot in installing htop.

Thanks alot!

---

### Post by mcduck on 2009-03-13
> **azzid said:**
> Oh, great to hear! But where is the memory going? Why doesn't it show up in top?
It's used as cache to store all data you have recently accessed, reducing the need to re-read it from the hard disk if you need it again.

And it *does* show in top, fifth line: "425324k cached" ;) It doesn't show in the program list because it doesn't belong to any of the running programs (actually, from program's point of view it can be seen as free memory as if any program needs more RAM some cached data is dropped to free the needed memory)

---

### Post by azzid on 2009-03-13
> **mcduck said:**
> It's used as cache to store all data you have recently accessed, reducing the need to re-read it from the hard disk if you need it again.

And it *does* show in top, fifth line: "425324k cached" ;)

Hmz, might start practicing on that 'reading' business again. ;)

I think I have found the source problem here, and it is very much tied to disk I/O:
```
root@ubuntu704:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             4.0G  3.8G     0 100% /home/user

```
I think there is a scheduled write to that disk that happens nightly, since the disk is full I guess Ubuntu does what it can to save the data by caching it in memory...

---

