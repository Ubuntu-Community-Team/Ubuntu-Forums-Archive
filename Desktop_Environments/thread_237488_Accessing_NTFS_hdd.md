---
title: "Accessing NTFS hdd"
date: 2006-08-16
forum: Desktop Environments
---

### Post by RobbieB on 2006-08-16
Greetings,
     I've been looking for a distro to run on my second hdd for awhile now, loving the idea behind the open source movement, and settled on Ubuntu. I have never used a OS different to Windows except for some Live CDs.

     Well I installed Ubuntu without a hitch but I can't seem to access my NTFS 250GB Windows hdd. At first it said it could not mount the drive and I found what I thought to be a solution by going System>Administration>Disks and 'enabling' the partition. It was already enabled however, so I disabled it and re-enabled it to make sure there wasn't a bug or anything. Well, my error message has changed, which isn't good because I found [this]("https://help.ubuntu.com/community/MountingWindowsPartitions") a minute ago.

     My error message now is:
```
You do not have the permissions necessary to view the contents of "disks-conf-sda1".
```
and it takes me to /tmp after a short delay.

     When I open Computer the hdd is called:
```
232.9 GB Volume: /tmp/disks-conf-sda1
```

Your help is appreciated :)

---

### Post by orb9220 on 2006-08-16
Well you need to edit your fstab. To that open a term and:

gksudo gedit /etc/fstab  Then find the line for your ntfs partition.
Mine is:

/dev/hda1       /media/hda1/     ntfs    defaults,nls=utf8,umask=007,gid=46 0       0

Which auto mounts and gives me read access since you cannot have write abilities in linux.

So highligt the ntfs line and copy and paste here and people then can help you.

---

