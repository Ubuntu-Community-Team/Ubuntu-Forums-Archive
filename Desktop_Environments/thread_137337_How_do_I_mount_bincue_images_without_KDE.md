---
title: "How do I mount bin/cue images without KDE?"
date: 2006-02-27
forum: Desktop Environments
---

### Post by lapsey on 2006-02-27
I have been through Mount-ISO and cdemu, yet cdemu only works to rip uncompressed audio tracks from audio cd images, and Mount-ISO only works with a KDE desktop.

I only hope the gnome people will address this sometime. 
In the meantime, is there any way mount bin/cues without installing KDE?

---

### Post by thomasando on 2006-02-27
```
mount -t loop /path/to/binfile.bin /mnt/cdrom
```

Pretty sure that'll do it...

Then access it by browsing to /mnt/cdrom

---

### Post by lapsey on 2006-02-28
sadly the mount sytax is wrong and I get errors on running mount with bin.

> modprobe loop ; sudo mount -o loop -t iso9660 /media/cdrom1/we.bin /media/iso

mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


---

### Post by lha on 2006-02-28
[QUOTE=lapsey]sadly the mount sytax is wrong and I get errors on running mount with bin.[/QUOTE]
Install [bchunk]("http://he.fi/bchunk/") from universe and use it to convert bins to isos.

---

### Post by lapsey on 2006-02-28
[QUOTE=lha]Install [bchunk]("http://he.fi/bchunk/") from universe and use it to convert bins to isos.[/QUOTE]

any idea on how to get it to convert from bin/cue audio cd into an ISO?

becasue no matter what I do it just extracts the audio tracks.

---

### Post by adamkane on 2006-03-31
Nautilus:
[http://www.ubuntuforums.org/showthread.php?t=149963](http://www.ubuntuforums.org/showthread.php?t=149963)

---

