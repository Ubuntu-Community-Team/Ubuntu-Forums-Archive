---
title: "Another DVD burning problem"
date: 2006-09-04
forum: Desktop Environments
---

### Post by ctcarton on 2006-09-04
I know there have been a lot of posts about burning problems, but I couldn't find any that were exatly the same as mine.

```
$ growisofs -dvd-compat -speed=16 -Z /dev/scd0 -dvd-video test
Executing 'mkisofs -dvd-video test | builtin_dd of=/dev/scd0 obs=32k seek=0'
INFO:   UTF-8 character encoding detected by locale settings.
        Assuming UTF-8 encoded filenames on source filesystem,
        use -input-charset to override.
/dev/scd0: "Current Write Speed" is 16.4x1385KBps.
  0.22% done, estimate finish Tue Sep  5 05:57:36 2006
  0.44% done, estimate finish Mon Sep  4 21:33:33 2006
  0.66% done, estimate finish Mon Sep  4 18:48:21 2006
  0.89% done, estimate finish Mon Sep  4 17:23:33 2006
  1.11% done, estimate finish Mon Sep  4 16:34:19 2006
  1.33% done, estimate finish Mon Sep  4 16:00:07 2006
...
...
 99.30% done, estimate finish Mon Sep  4 13:15:53 2006
 99.52% done, estimate finish Mon Sep  4 13:15:52 2006
 99.74% done, estimate finish Mon Sep  4 13:15:52 2006
 99.96% done, estimate finish Mon Sep  4 13:15:53 2006
Total translation table size: 0
Total rockridge attributes bytes: 0
Total directory bytes: 2048
Path table size(bytes): 26
Max brk space used 21000
2260811 extents written (4415 MB)
builtin_dd: 2260816*2KB out @ average 8.4x1385KBps
/dev/scd0: flushing cache
/dev/scd0: closing track
/dev/scd0: closing disc
:-( unable to reload tray: No such device or address


/var/log/messages:
Sep  4 13:11:30 localhost kernel: [4365781.602000] usb 5-2: reset high speed USB device using ehci_hcd and address 4
Sep  4 13:11:37 localhost kernel: [4365788.659000] scsi: Device offlined - not ready after error recovery: host 2 channel 0 id 0 lun 0


```

And then eject won't work: "[COLOR="Red"]eject: unable to open `/dev/scd0[/COLOR]'".  I have to power cycle the drive (I'm using an external usb burner) to get eject to work, and the disk is unreadable! The same thing seems to happen with k3b.

Anyone have any advice?

---

### Post by littlespy on 2006-09-04
I've had a lot more success with nero for linux than growisofs, I think you can download a trial from their website.

---

### Post by ctcarton on 2006-09-05
neroLINUX worked perfectly, thank you.

---

