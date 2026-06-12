---
title: "backups"
date: 2008-07-30
forum: Desktop Environments
---

### Post by gardengxc on 2008-07-30
are there any programs to backup my ubuntu so I don't loose some thing important again and have to reinstall? something like windows system restore or macs time machine?

---

### Post by wannadumpwindows on 2008-07-30
Have a look at sbackup. 

Search for it in synaptic package manager.

It's pretty simple to use, and you can store your back-ups just about anywhere.

---

### Post by Carl H on 2008-07-30
I just use rsync to backup my home directory to another drive.

```
rsync -av /home/carl/ /backup
```

---

### Post by spupy on 2008-07-30
Check out the program [PartImage]("http://www.partimage.org/Main_Page"). It can backup and restore whole partitions. It basically makes an archive from the selected partition, and you can record this archive on a DVD. Later use the same program to restore the image.

PartImage is part of the [Linux System Rescue CD]("http://www.sysresccd.org/Main_Page"). It is a Live CD with very helpful tools, for use when, well, when your system needs rescue. :)

---

### Post by Rhubarb on 2008-07-30
I find Unison is quite good
```
sudo aptitude install unison-gtk
```
It can backup to a local directory, or ssh to a remote computer.
It can backup changes in both directions, and has a nice graphical user interface (gui).

---

### Post by gardengxc on 2008-07-31
thanks for the list, but do any of thees not require my input. I would like it to do a backup often on its own so I don't forget to.

---

### Post by Carl H on 2008-07-31
You can use cron to schedule it to run a backup job on a regular basis. 

[https://help.ubuntu.com/community/CronHowto]("https://help.ubuntu.com/community/CronHowto")

---

