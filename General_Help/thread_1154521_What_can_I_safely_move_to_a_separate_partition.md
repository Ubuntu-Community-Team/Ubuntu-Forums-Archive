---
title: "What can I safely move to a separate partition?"
date: 2009-05-09
forum: General Help
---

### Post by Cephi on 2009-05-09
I had decided not to get an EeePC 901 due to storage limitations.  But after finding out that I can move my home folder to a separate partition (see [http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")), I'm stoked to get one.  It has one 4Gb SSD, and a secondary, slower 8Gb SSD.  I'll be booting from the 4Gb, but I'll move my home directory to the 8Gb and mount it at /home.

What I'm trying to figure out now is whether there are any other space hogs that can be treated in the same way, putting them on a separate partition (on the 8Gb SSD) and then mounting them in their customary locations -- without making a noticeable impact on system performance.  So, /usr/bin?  /usr/java?  Are those terrible ideas?  Anyone have other/better ideas?  Suggestions would be much appreciated.  (I'll be running xubuntu 9.04 btw.)

(PS I'm equally stoked about being able to boot different linux flavors from SD cards all sharing the same /home dir!)

---

### Post by Altay_H on 2009-05-09
I don't know the full extent of what can safely be moved to its own partition, but I know that /var can. I have three partitions in my installation:
/
/var
/home


EDIT:
Some more safe partitions:
/usr
/root
/tmp
/boot
Sources: [http://www.linuxforums.org/forum/installation/119276-moving-directories-folders-separate-partitions.html](http://www.linuxforums.org/forum/installation/119276-moving-directories-folders-separate-partitions.html)
[http://lissot.net/partition/partition-04.html]("http://lissot.net/partition/partition-04.html")

---

### Post by dcstar on 2009-05-09
> **Cephi said:**
> 
..........
What I'm trying to figure out now is whether there are any other space hogs that can be treated in the same way, putting them on a separate partition (on the 8Gb SSD) and then mounting them in their customary locations -- without making a noticeable impact on system performance.
..........

Totally pointless unless you **desperately** require space on the drive for something else.

Moving /home means it is independent of future installs/reinstalls and puts something that may hold a lot of data outside of the root partition so it makes sense to do that (it should probably be the default for all installs anyway).

Moving anything else will just fragment the limited storage space - wasting some of that space - and provide no performance gains at all.

---

### Post by Alterax on 2009-05-09
Theoretically anything beyond /boot can be moved; the changes just need to be posted in /etc/fstab.

Fragmentation isn't (as others pointed out) is not necessarily a good thing.  However, for safety reasons, fragmentation can also be quite useful.  Often, I keep the /var and /home directories broken out into their own partitions, since /var is where my in-house repository and databases are it gets hefty, and /home is full of the cruft that I accumulate.

Breaking these out gives the O.S. a little bit of wiggle room.  If the drive is completely full, it's a pain to boot into single-user mode, track down the stuff that's filled up the drive and delete it.  Breaking them out like this makes it easier to correct the problems while keeping the system up.

So breaking them out for performance can be iffy--has its good points and its bad points.  Usually it's done for stability or for adding more space without having to reinstall the entire OS.

---

### Post by Cephi on 2009-05-10
/var sounds good.  /root, /tmp and /boot are too small to be worth it, imo.  All of /usr would definitely be big enough to make a big difference, but I worry it would slow system performance noticeably. I don't really know enough, though, to have good justification for that worry.

> **dcstar said:**
> Totally pointless unless you **desperately** require space on the drive for something else. 

...

Moving anything else will just fragment the limited storage space - wasting some of that space - and provide no performance gains at all.
> **Alterax said:**
> So breaking them out for performance can be iffy--has its good points and its bad points.  Usually it's done for stability or for adding more space without having to reinstall the entire OS.
I'm not after performance gains.  I'm going to be booting from a 4Gb drive (as I am now on my EeePC 701).  I already can't install everything I'd like to install, because of space limitations.  I just want the space, not performance gains, and I don't care about wasting a bit of the 8Gb SSD space.  The only thing I'm worried about is performance losses.  Does anyone think it would significantly degrade system performance to move /var or /usr to the slower SSD?

---

