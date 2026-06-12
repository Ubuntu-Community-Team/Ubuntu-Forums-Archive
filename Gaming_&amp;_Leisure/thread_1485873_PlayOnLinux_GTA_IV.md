---
title: "PlayOnLinux GTA IV"
date: 2010-05-17
forum: Gaming &amp; Leisure
---

### Post by H0lyGanGs7eR on 2010-05-17
Hello, i'm trying to install GTA IV, but i can't mount the iso files. I tried with Gmount-iso , but it didn't work. I tried through console and i got this error. My /data/ is a NTFS partition. Is it possible to be a problem? Please help I love this game! 
```
niki@niki-desktop:/data/Downloads/GTA.IV.MULTi-KiNGS$ sudo mount -o loop -t iso9660 GTA\ IV\ DVD\ 1.iso /data/mountcdrom/
[sudo] password for niki: 
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

niki@niki-desktop:/data/Downloads/GTA.IV.MULTi-KiNGS$ dmesg | tail
[19187.783606] ISOFS: Unable to identify CD-ROM format.
[19235.338706] ISOFS: Unable to identify CD-ROM format.
[19257.522621] end_request: I/O error, dev fd0, sector 0
[19257.552548] end_request: I/O error, dev fd0, sector 0
[19261.942559] end_request: I/O error, dev fd0, sector 0
[19261.972540] end_request: I/O error, dev fd0, sector 0
[19272.012555] end_request: I/O error, dev fd0, sector 0
[19272.032584] end_request: I/O error, dev fd0, sector 0
[19327.678042] ISOFS: Unable to identify CD-ROM format.
[20111.478606] ISOFS: Unable to identify CD-ROM format.

```

---

