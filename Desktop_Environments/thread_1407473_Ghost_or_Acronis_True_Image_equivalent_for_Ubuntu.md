---
title: "Ghost or Acronis True Image equivalent for Ubuntu?"
date: 2010-02-15
forum: Desktop Environments
---

### Post by hhtmp88 on 2010-02-15
Dear all,

I use Ghost 12.0 or Acronis True Image 10.0 for system backup of WinXP
-> so any equivalent application for Ubuntu?

Thanks for any kind of help!
Rgds,

---

### Post by howefield on 2010-02-15
Clonezilla

clonezilla.org

Doesn't have the nice graphical interface of Acronis, but it is very effective.

---

### Post by hhtmp88 on 2010-02-15
Thanks  howefield for your advice!

---

### Post by little_penguin on 2010-08-05
Partimage is also good for full partition image backups.

---

### Post by hhtmp88 on 2010-08-05
where to download "Partimage"?

---

### Post by little_penguin on 2010-08-05
Partimage is included on many live CDs, because the partition you want to backup cannot be mounted or in use at the time so in most cases you have to use a live CD. I use either System Rescue Live CD, Gparted Live CD or Parted Magic Live CD. Partimage is on all of these disks. You can find ISOs for these live CDs using a linux torrent search engine (e.g. linuxtracker.org), download one, burn the ISO to a CD and boot from it. There is more information on the partimage website:

[http://www.partimage.org]("http://www.partimage.org/")

Regards,
LP

---

### Post by jaeger2000 on 2010-11-01
-Package sbackup can perform full backup of files and system settings.
-No cloning of disk though.

sudo apt-get install sbackup

kind regards,
Ian Gregory, Sydney.

---

### Post by hhtmp88 on 2010-11-27
Thanks jaeger2000!

sbackup seems a good tools for me if it has auto backup functions
-> e.g backup, everytime, I shutdown my computer

Rgds,

---

### Post by asmoore82 on 2010-11-27
[SIZE="3"]Big +1[/SIZE] for Clonezilla.

Clonezilla includes partimage along with every other open-source imaging tool imaginable.

---

