---
title: "Do data discs need to reserve space for root?"
date: 2009-06-25
forum: General Help
---

### Post by ticket on 2009-06-25
I am adding a separate data disc to my system, to store videos, etc.
To format the disc, a command like this is often used:

mke2fs -m 0 -j /dev/sda1

The option "-m" means (from the man page):

> -m reserved-blocks-percentage
Specify the percentage of the filesystem blocks reserved for the
super-user.  **This avoids fragmentation**,  and  allows  root-owned
daemons,  such  as syslogd(8), to continue to function correctly
after non-privileged processes are prevented from writing to the filesystem.  The default percentage is 5%.

So a "-m 0" means no space is allocated for root. As this is a data disc and not a system disc, I assume this will be ok, as it makes more storage space available.  

But, would using "-m 0" cause fragmentation problems for the data disc as it gets nearly full?

---

### Post by TeoBigusGeekus on 2009-06-25
Why don't you use gparted for God's sake?

---

### Post by mcduck on 2009-06-25
> **ticket said:**
> I am adding a separate data disc to my system, to store videos, etc.
To format the disc, a command like this is often used:

mke2fs -m 0 -j /dev/sda1

The option "-m" means (from the man page):



So a "-m 0" means no space is allocated for root. As this is a data disc and not a system disc, I assume this will be ok, as it makes more storage space available.  

But, would using "-m 0" cause fragmentation problems for the data disc as it gets nearly full?

No, you don't need to reserve any disk space for root on others than the system partitions.

And yes, you'll get fragmentation if the disk gets full. But you will get that no matter if some amount of disk space is reserved for root or not, as fragmentation starts to slow the filesystem down long before you manage to fill the disk to the default 95% limit.

---

### Post by mcduck on 2009-06-25
> **TeoBigusGeekus said:**
> Why don't you use gparted for God's sake?

Why would he use Gparted? The reason why different tools exist is that different people prefer different ways of using the computer. And command-line definitely is the most flexible and powerful way of doing things so it's just normal that many people prefer it over graphical interfaces.

Besides, using Gparted instead of CLI tools wouldn't even answer the actual question.. :D

---

### Post by egalvan on 2009-06-25
> **TeoBigusGeekus said:**
> Why don't you use gparted for God's sake?

Choice.

---

### Post by ticket on 2009-06-25
> **mcduck said:**
> No, you don't need to reserve any disk space for root on others than the system partitions.

Thanks mcduck, and all the others for such a quick response!

I did originally use gparted, but doing that didn't explain why it had lost me 5% of the disc volume space. I'm not sure if gparted gives you the option to use "-m 0", but no matter - I am equally comfortable with the command line once I understand the options. The man page on  mke2fs was a bit ambiguous on the "-m" option (sounds like it was written with system discs in mind), that's why I posted the question.

Thanks guys!

---

### Post by ticket on 2009-06-25
One other query:  mke2fs supports this option:

```
 -c     Check the device for bad blocks before creating the file system.
```

e.g. 
 
mke2fs -m 0 -j -c /dev/sdb1

Is this option worthwhile putting in?  If you don't use it, what happens when a bad block is encountered?

---

### Post by mcduck on 2009-06-25
> **ticket said:**
> One other query:  mke2fs supports this option:

```
 -c     Check the device for bad blocks before creating the file system.
```

e.g. 
 
mke2fs -m 0 -j -c /dev/sdb1

Is this option worthwhile putting in?  If you don't use it, what happens when a bad block is encountered?
If you use that option, any bad blocks will be excluded from the file system. If you don't the bad blocks are included in the file system like they usually would be, meaning that any data written on those blocks will corrupt.

That option is pretty much just a workaround to allow using drives that have bad blocks without (immediately) corrupting your data, but drives with bad blocks tend to generate more bad blocks over time (or fail completely) so that option doesn't really make using such drive safe in the long run.

Personally, if I suspected any of my drives having bad blocks I'd buy a new drive as soon as possible.

Of course if you are not in hurry you could enable the option just for the benefit of getting a report if there are any bad blocks on your drive. ;)

---

### Post by ticket on 2009-06-25
Yes, I suspect these days the -c option is not needed for modern hard disc drives.  I found this:

[PHP]...SCSI and IDE drives have bad block logic on-board, so you are safe there.[/PHP] 

[http://docs.rinet.ru/RedHatu/rhl05.htm](http://docs.rinet.ru/RedHatu/rhl05.htm)

---

### Post by TeoBigusGeekus on 2009-06-26
Sorry everyone for my attitude - I never meant to be offensive or arrogant, just trying to indicate the easiest way to do it.
Sorry again!!!

---

### Post by Divider on 2009-06-26
> **egalvan said:**
> Choice.

Amen to that.

---

