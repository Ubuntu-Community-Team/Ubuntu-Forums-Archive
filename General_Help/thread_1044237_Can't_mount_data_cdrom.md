---
title: "Can't mount data cdrom"
date: 2009-01-19
forum: General Help
---

### Post by DJ_Peng on 2009-01-19
I was going through my old Windows catalog of disks I'd burned and I realized one of them hadn't been cataloged in my GNOME Disk Catalog, but when I put it in my DVD drive it never became available to the system. I tried it on a roomie's WinXP box and it showed the disk as being writable. That's odd because it's definitely been burned already and it's not a CD-RW.

Today I did a search on the forums and found a thread in the archive section that had a [pair of commands to run]("http://ubuntuforums.org/showpost.php?p=4436384&postcount=5") in dual terminal windows. ```
sudo cat /proc/kmsg
``` did nothing, but when I ran ```
sudo mount -t auto /dev/cdrom /media/cdrom/
``` I got this
> :~$ sudo mount -t auto /dev/cdrom /media/cdrom
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: you must specify the filesystem typeI burned it with a Windows app, although it was several years ago and I don't remember what program I used. Can anyone recommend a way to fix the problem? It turns out I have some MP3's on that disk that never made it back into my library after I started converting my WMA's to Ogg Vorbis files so I need to either recover them from the disk or track them down and buy them from Amazon's MP3 store, if they even have all of them.

ETA: I would have posted this query on the thread I found, but it's in the archive system so I couldn't add to it.

---

### Post by taurus on 2009-01-19
Try including the filesystem when you mount it.

```
sudo mount -t iso9660 /dev/cdrom /media/cdrom
```

---

### Post by adamlau on 2009-01-19
Verify /media/cdrom exists and change 'auto' to either 'udf', or 'iso9660'.

---

### Post by DJ_Peng on 2009-01-19
> **taurus said:**
> Try including the filesystem when you mount it.
That's part of what I'm trying to get, if there's a way to find out what filesystem is used.

> **adamlau said:**
> Verify /media/cdrom exists and change 'auto' to either 'udf', or 'iso9660'.
Tried both, both failed with 
> mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or soTrying the dmesg gets me
> :~$ dmesg |tail
[73678.382039] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[73678.382056] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
[73678.382063] sr 1:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[73678.382070] end_request: I/O error, dev sr0, sector 68
[73678.382129] isofs_fill_super: bread failed, dev=sr0, iso_blknum=17, block=17

---

