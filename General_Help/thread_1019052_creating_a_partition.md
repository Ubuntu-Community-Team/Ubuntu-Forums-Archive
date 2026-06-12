---
title: "creating a partition?"
date: 2008-12-22
forum: General Help
---

### Post by NuBiXx on 2008-12-22
(New to Ubuntu) So I fully made the switch to ubuntu and forgot to create a second partition for backups and I was wondering what would be the easiest way to create a partition? thanks

---

### Post by taurus on 2008-12-22
Use gparted from the LiveCD or GParted LiveCD, [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php).

---

### Post by drs305 on 2008-12-22
> **NuBiXx said:**
> (New to Ubuntu) So I fully made the switch to ubuntu and forgot to create a second partition for backups and I was wondering what would be the easiest way to create a partition? thanks

For a gui-based app, gparted. It's accessed via the main menu: System > Adminstration > Partition Editor. However, you cannot use it while you are using the normal ubuntu system. You will either need to boot from the LiveCD or use a gparted or systemrescuecd.

Welcome to ubuntu, by the way.

---

### Post by NuBiXx on 2008-12-22
OK thanks very much..

---

### Post by NuBiXx on 2008-12-22
Thanks again I successfully created a ext2 partition, I have a couple more question what user friendly program should I use to create backups? I did a search on the forums and read a user suggested compressing the entire partition but I think this would take a very long time (11gigs) so I am hoping to use a image program of sorts.

@drs305 thanks for the Welcome :)

---

### Post by drs305 on 2008-12-22
Partimage and clonezilla are two that are often mentioned for imaging. I use partimage on 6GB of data and it takes about 10 minutes to use the medium compression level. For backing up by syncing files many use rsync.

For a good partimage tutorial, see this link:
[http://www.psychocats.net/ubuntu/partimage]("http://www.psychocats.net/ubuntu/partimage")

---

