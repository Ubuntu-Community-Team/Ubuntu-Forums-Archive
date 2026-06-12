---
title: "DVD not recognized"
date: 2006-09-30
forum: Desktop Environments
---

### Post by ropers on 2006-09-30
I have a Pioneer DVD-116 ATAPI DVD-ROM drive.
It can play some of my DVDs, but I cannot get my [AI]("http://www.imdb.com/title/tt0212720/") DVD to play. Since the DVD is region code restricted (region code 2), I first suspected that to be the problem:

```
ropers@tranquility:~$ regionset
regionset version 0.1 -- reads/sets region code on DVD drives
ERROR: Could not open disc "(null)"!
Please ensure there is a readable CD or DVD in the drive.

```

So the region code doesn't seem to be the issue. I then tried to manually mount the DVD:

```
ropers@tranquility:~$ sudo mount -t iso9660 /dev/hdb /cdrom
Password:
mount: No medium found

```

It seems as if the drive is acting as if there were no DVD inserted whenever I use that particular DVD. The DVD works fine in other systems and other DVDs work fine in the Ubuntu "Dapper" 6.06 LTS system I am having this problem with. 

Any ideas?

PS: from the dmesg:

```
[17179576.908000]     ide0: BM-DMA at 0x4000-0x4007, BIOS settings: hda:DMA, hdb:DMA

[17179577.644000] hdb: Pioneer DVD-ROM ATAPIModel DVD-116 0122, ATAPI CD/DVD-ROM drive

[17179578.408000]  hdc:<6>hdb: ATAPI 40X DVD-ROM drive, 256kB Cache, UDMA(33)
```

---

