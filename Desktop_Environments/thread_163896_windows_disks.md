---
title: "windows disks"
date: 2006-04-21
forum: Desktop Environments
---

### Post by aptsonic on 2006-04-21
why is it when i place a disk in my system made for windows nothing shows up?
is there a way i can add the ability to read window disks?

---

### Post by aptsonic on 2006-04-21
by window's disks i mean game or software disks that are ordinarily meant for windows....

---

### Post by towsonu2003 on 2006-04-21
I'm not sure if I understand the problem but

if you expect that ubuntu will launch games when a windows game CD is inserted, windows programs won't play in linux unless you try wine (or similar) or qemu (or similar). But I don't think this is your problem (so I'm not elaborating). is it?

if you expect ubuntu to automount CDs and launch nautilus for you to browse the CD, this should be the case (although I somehow lost this feature in my system). To mount the CD to browse:
```

sudo mount /media/cdrom0

```
then go to Places>Computer>CD-ROM Drive
if above command does not work, pls post the output of 
```

cat /etc/fstab

```

Also check out a nice tool for automounting and other stuff:
System>Preferences>Removable Drives and Media

---

### Post by aptsonic on 2006-04-21
[QUOTE=towsonu2003]I'm not sure if I understand the problem but

if you expect that ubuntu will launch games when a windows game CD is inserted, windows programs won't play in linux unless you try wine (or similar) or qemu (or similar). But I don't think this is your problem (so I'm not elaborating). is it?

if you expect ubuntu to automount CDs and launch nautilus for you to browse the CD, this should be the case (although I somehow lost this feature in my system). To mount the CD to browse:
```

sudo mount /media/cdrom0

```
then go to Places>Computer>CD-ROM Drive
if above command does not work, pls post the output of 
```

cat /etc/fstab

```

Also check out a nice tool for automounting and other stuff:
System>Preferences>Removable Drives and Media[/QUOTE]


sorry my brain isn't attached to my body today. my problem right now isn't that my cdrom isn't mounting, its that when i place a disk in the drive i'm not able to see any of the information on the disk. 

for example right now i want to play master of orion 3 through wine, but i can't get any of the installing files from the cd's.

---

### Post by aptsonic on 2006-04-21
ah nm... i think i figured out the problem...

in the disk manager under admin, the drive wasn't accessible... stupid little problems.

---

### Post by towsonu2003 on 2006-04-21
so this is solved? :)

---

### Post by aptsonic on 2006-04-21
[QUOTE=towsonu2003]so this is solved? :)[/QUOTE]

yeah now only if i can get it to install with wine correctly

thanks!

---

