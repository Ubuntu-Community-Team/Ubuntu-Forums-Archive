---
title: "How do I mount a second hard drive?"
date: 2006-03-29
forum: Desktop Environments
---

### Post by ardchoille on 2006-03-29
I have a second 160Gb hard drive (/dev/hdb) that I use to hold packages and daily backups. What I have been doing is manually mounting this drive, copying the daily backups over then unmounting it. However, I thought about something.

My backup scheme is thus:
```

cd /home
tar -cjf /home/backups/current.home.tar.bz2 myuser
mv /home/backups/current.home.tar.bz2 /home/backups/`date +%Y%m%d`.myuser.tar.bz2

```
and this works great for me. I am wondering if it's possible to just keep the second drive mounted (mount on boot) and just mv the backups to the second drive.

So, my questions are:

1) How do I make this second drive mount when the computer is booted?
2) Sometimes we have power outages. Would there be any danger to the second drive or its contents if the power cuts out while it's mounted?
3) Are there any other things I need to be concerned about?

---

### Post by ispmarin on 2006-03-29
Hello there. You can add a line on you /etc/fstab, like this:

/dev/hdb1    /home/backup     reiserfs     defaults         0           0

I am supposing that the file system type is reiserfs, what I think is the best file system type for you operation (It if another filesystem, like ext3, just put ext3 of vfat if it is fat32). It is fast, and the journaling system tries hard to mantain consistency even when the system is shut down uncleanly or forced (like a power outage). But of course will have some danger involved. Here at my lab a reiserfs partition survived very well on several forced reboots, with no problems at all.

---

### Post by ardchoille on 2006-03-29
[QUOTE=ispmarin]Hello there. You can add a line on you /etc/fstab, like this:

/dev/hdb1    /home/backup     reiserfs     defaults         0           0

I am supposing that the file system type is reiserfs, what I think is the best file system type for you operation (It if another filesystem, like ext3, just put ext3 of vfat if it is fat32). It is fast, and the journaling system tries hard to mantain consistency even when the system is shut down uncleanly or forced (like a power outage). But of course will have some danger involved. Here at my lab a reiserfs partition survived very well on several forced reboots, with no problems at all.[/QUOTE]
So this should work ok?

/dev/hdb1       /mnt/hdb1               ext3    defaults,errors=remount-ro 0       1

---

### Post by ispmarin on 2006-03-29
I think that you dont neet the error=remount option and should set the last two parameters to 0 and 0. Otherwise, should work.

---

### Post by ardchoille on 2006-03-29
[QUOTE=ispmarin]I think that you dont neet the error=remount option and should set the last two parameters to 0 and 0. Otherwise, should work.[/QUOTE]
Ok, looks like that was it. Thank you very much :)

---

### Post by ispmarin on 2006-03-29
You are welcome...

---

