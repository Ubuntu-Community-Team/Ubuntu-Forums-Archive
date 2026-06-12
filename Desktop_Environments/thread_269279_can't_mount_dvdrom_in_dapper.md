---
title: "can't mount dvdrom in dapper"
date: 2006-10-01
forum: Desktop Environments
---

### Post by joemseat on 2006-10-01
Hi everybody,

I can't seem to mount my dvdrom drive anymore. The drive is a pioneer dvr-110. Here is some output:

```
joem@seat:~$ sudo mount -t iso9660 /dev/hda /media/cdrom0
mount: block device /dev/hda is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

joem@seat:~$ dmesg | tail
[17359470.208000] attempt to access beyond end of device
[17359470.208000] hda: rw=0, want=7398320, limit=4
[17359470.208000] attempt to access beyond end of device
[17359470.208000] hda: rw=0, want=1252, limit=4
[17359470.208000] attempt to access beyond end of device
[17359527.612000] attempt to access beyond end of device
[17359527.612000] hda: rw=0, want=68, limit=4
[17359527.612000] isofs_fill_super: bread failed, dev=hda, iso_blknum=16, block=16

```

The strange thing is that while I cannot mount it in dapper, my windows xp virtual machine running in vmware on the same machine has no problem reading from the drive!

When I put blank media in the drive, it is correctly detected and I am asked if I want to burn a cd/dvd.

Thanks for the help :)

---

### Post by orb9220 on 2006-10-01
Try

sudo mount -t iso9660 -o loop <FILENAME.iso> /media/cdrom

---

### Post by joemseat on 2006-10-01
orb9220, that works but my problem isn't mounting images, it is mounting the drive itself when there is a disk in it.

---

### Post by orb9220 on 2006-10-01
Sorry didn't read close enough. Me go hide in closet now.

---

### Post by joemseat on 2006-10-02
i figured it out, for the record:

vmware was 'in control' of the drive - just disconnect it in the vmware console and that fixed it :)

---

