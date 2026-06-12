---
title: "NTFS Mount - Odd Behavior"
date: 2009-03-10
forum: General Help
---

### Post by SlightyAnnoyed on 2009-03-10
I hope you might provide a little help. I am trying to automount two external HDD formatted with NTFS (along with two others HDD, a linux only, and an NTFS). Originally, I had all the harddrives mounting correctly, then for some reason only one of the external's will mount. The odd part is every time I restart the computer, the external that mounts will change. The first will mount, and the second wont, then vice versa on next restart. I find this annoying and slightly amusing at the same time. I included my fstab.

*NOTE* The externals are "J" and "R"

```
proc /proc proc defaults 0 0
# Entry for /dev/sdb1 :
UUID=deb33133-b3f3-48ab-a8c1-6787e41bd34b / ext3 errors=remount-ro 0 1
# Entry for /dev/sdb6 :
UUID=6f2427d6-d54e-4cac-888b-724d931ea454 /var/lib xfs defaults 0 2
# Entry for /dev/sdb5 :
UUID=f436eef1-2d0e-4c74-8794-96fc83b47b81 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

#Entry for MrMedia
LABEL=DISK1_VOL1 /media/MrMedia ntfs-3g defaults,rw 0 0
#Entry for R
UUID=C630F5A330F59B1F /media/R ntfs-3g defaults,rw,nls=utf8 0 0
#Entry for J
UUID=C6EC36A1EC368C25 /media/J ntfs-3g defaults,rw,nls=utf8 0 0
```

---

### Post by SlightyAnnoyed on 2009-03-11
Anybody that can help? I have cookies...

---

### Post by vanadium on 2009-03-11
A very likely cause for an ntfs formatted drive that does not automount is that it has not been properly disconnected at some time. Solution: connect to a windows system and properly disconnect using the "safely remove hardware" icon. If it does not yet work, repeat the proces, and also perform a file system check using the windows file checking tools before disconnecting the drive.

---

### Post by SlightyAnnoyed on 2009-03-11
turns out it just fixed itself somehow...

but if it pops up again, that will definitely be the first thing I try, thanks

---

