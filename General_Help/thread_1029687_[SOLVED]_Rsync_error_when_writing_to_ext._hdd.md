---
title: "[SOLVED] Rsync error when writing to ext. hdd"
date: 2009-01-03
forum: General Help
---

### Post by jdavis72 on 2009-01-03
I have been trying to make complete home directory backups to an external hdd on my desktop system. However, when I use use rsync directly, or use FlyBack, I keep getting this error at the end:
```
rsync: writefd_unbuffered failed to write 4 bytes [sender]: Broken pipe (32)
rsync: symlink "/media/truecrypt1/flyback/20090103_112414.backup/home/username/.kde/cache-desktopa" -> "/var/tmp/kdecache-username" failed: Operation not permitted (1)
rsync: write failed on "/media/truecrypt1/flyback/20090103_112414.backup/home/username/.VirtualBox/Machines/WinXP Pro/Snapshots/{62cde4ef-1e34-4ec9-dfbb-497ecce240be}.vdi": File too large (27)
rsync error: error in file IO (code 11) at receiver.c(298) [receiver=3.0.3]
rsync: symlink "/media/truecrypt1/flyback/20090103_112414.backup/home/username/.kde/socket-desktop" -> "/tmp/ksocket-username" failed: Operation not permitted (1)
rsync: symlink "/media/truecrypt1/flyback/20090103_112414.backup/home/username/.kde/tmp-desktop" -> "/tmp/kde-username" failed: Operation not permitted (1)
rsync: connection unexpectedly closed (2170 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(635) [sender=3.0.3]
```
Is it simply a matter of a file being too large? What about copying symlinks? What am I doing wrong? This is on Ubuntu 8.10 writing to a ext usb sata hdd. The desktop hdd is ext3 and is fully encrypted with luks (using the ubuntu 8.10 alt cd). The ext hdd is also ext3 and fully encrypted with Truecrypt 6.1a. Thanks in advance!

Jeremy

---

### Post by jdavis72 on 2009-01-05
Finally figured it out. My TrueCrypt volume was formatted at FAT32, which of course has a large file size limit. When rsync encountered this, it failed. After reformatting the drive without encryption to ext3, rsync worked.

---

