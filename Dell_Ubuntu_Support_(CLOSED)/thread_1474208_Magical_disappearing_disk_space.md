---
title: "Magical disappearing disk space"
date: 2010-05-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by D0M1N8 on 2010-05-05
Hey guys, super linux newb here. I recently switched to Ubuntu Karmic from Windows Vista, and I've been really, really happy so far. Unfortunately, i've run into a problem.

The disk usage analyzer shows that I have over 96 gigs available on my hard drive, but when I go to the properties window on my home folder, it says I only have 1gb available!!

I'm trying to install tf2 on steam, and it's kind of hard with about 1 gig. Any ideas?

Thanks.

EDIT: Okay, I figured out the problem. I running ubuntu using wubi because my dimension E520 was having serious problems with the live cd. Now I need to know how to increase the amount of space I can use in wubi. Did that make sense?

---

### Post by mikewhatever on 2010-05-05
Applications->Accessories->Terminal, and please post the output of **df -h**   .

---

### Post by D0M1N8 on 2010-05-05
Here it is:

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0             17G   14G  1.6G  90% /
udev                 1006M  320K 1006M   1% /dev
none                 1006M  4.1M 1002M   1% /dev/shm
none                 1006M  204K 1006M   1% /var/run
none                 1006M  4.0K 1006M   1% /var/lock
none                 1006M     0 1006M   0% /lib/init/rw
/dev/sda3             223G  122G  102G  55% /host
/dev/sr1              114M  114M     0 100% /media/cdrom1

```

---

### Post by mikewhatever on 2010-05-05
Well, apparently, you can resize the virtual partition Ubuntu is installed to with LVPM.
[http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)

That said, wubi is not really ideal for a long term usage. It's great for trying out and testing, but if you plan on sticking with Ubuntu, I'd recommend installing to a real partition.

... and the code tags are just 'code' '/code' in square brackets;)

---

### Post by D0M1N8 on 2010-05-06
Thanks, I'll give it a try.

---

