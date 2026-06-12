---
title: "Dell XPS M1530 Can't burn DVD"
date: 2009-06-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Gremmie on 2009-06-04
I have a Dell XPS M1530 that I bought through Dell with Ubuntu 8.04 LTS. I tried to burn a DVD for the first time last night and could not. Basically the system doesn't recognize that a blank DVD has been inserted. I insert the disc, it spins for a while, then nothing. Normally, as I understand it, a blank DVD icon should appear on the desktop. I tried to use several software packages to burn a DVD but they all thought no disc was in the drive.

I used lshw to see that my system did recognize my DVD drive as being a DVD drive with write capabilities. I tried both DVD+RW and DVD-R media. It can read CD's and play DVD movies just fine. I looked in the system log, and whenever the blank DVD is inserted it just spews CRC errors every 2 or 3 seconds. The drive is listed as being "open", not "nodisc" with the blank media inserted.

Any ideas? I'm thinking about re-imaging with the 9.04 Dell ISO as a last resort. Thanks.

---

### Post by Gremmie on 2009-06-05
Here is some more data. After I insert the blank DVD media and nothing happens, I run these commands:

```

brian@gremmie:~$ sudo lshw -C disk
 *-cdrom
      description: DVD-RAM writer
      product: DVD+-RW UJ-875S
      vendor: MATSHITA
      physical id: 0.0.0
      bus info: scsi@0:0.0.0
      logical name: /dev/cdrom
      logical name: /dev/dvd
      logical name: /dev/scd0
      logical name: /dev/sr0
      version: D200
      capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
      configuration: ansiversion=5 status=open

```

If I look in /var/log/syslog I see these messages over and over:

```

Jun  4 20:30:50 gremmie kernel: [  828.470461] sr0: CDROM (ioctl) error, command: Test Unit Ready 00 00 00 00 00 00
Jun  4 20:30:50 gremmie kernel: [  828.470480] sr: Sense Key : Hardware Error [current]
Jun  4 20:30:50 gremmie kernel: [  828.470487] sr: Add. Sense: Id CRC or ECC error

```

A Dell hardware technician said this was a software issue, but I'm not sure how he knew that. Should I upgrade to 9.04?

---

### Post by Gremmie on 2009-06-05
I tried a Memorex DVD+R and I was able to burn an ISO. 

The DVD-R I tried earlier was a Verbatim brand. Is there really this much variability in the Linux world?

In any event, I'm glad my hardware doesn't seem to be broken.

---

