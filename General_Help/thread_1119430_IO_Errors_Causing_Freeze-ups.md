---
title: "I/O Errors Causing Freeze-ups"
date: 2009-04-07
forum: General Help
---

### Post by pirattrev on 2009-04-07
every now and then my laptop (Thinkpad T61) encounters these severe I/O and disk read errors. My system monitor tops with complete i/o wait and nothing can be used. It seems to happen randomly at times, and other times when opening videos with VLC, or refreshing my quodlibet library. Occasionally it gets very bad and even in TTY all commands are worthless because of the flood of error messages. Even after Hardy auto-corrects and claims the filesystem is clean the problem resurfaces only a little bit later (in one case on next reboot). I've also noticed the situation also freezes on GDM start, and rebooting it sometimes unfreezes the problem.

Here's the flooding error msg:
```

Apr  7 02:55:04 tardis kernel: [ 3050.624695] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr  7 02:55:04 tardis kernel: [ 3050.624707] ata1.00: BMDMA stat 0x4
Apr  7 02:55:04 tardis kernel: [ 3050.624718] ata1.00: cmd c8/00:00:5f:2d:9f/00:00:00:00:00/e1 tag 0 dma 131072 in
Apr  7 02:55:04 tardis kernel: [ 3050.624722]          res 51/40:00:ec:2d:9f/00:00:00:00:00/e1 Emask 0x9 (media error)
Apr  7 02:55:04 tardis kernel: [ 3050.624728] ata1.00: status: { DRDY ERR }
Apr  7 02:55:04 tardis kernel: [ 3050.624732] ata1.00: error: { UNC }
```

any ideas?

---

### Post by lykwydchykyn on 2009-04-07
Try running badblocks to check for bad sectors on the drive:
```

sudo badblocks -v /dev/sda

```

You might want to install the smartmontools package and to a S.M.A.R.T. check on the drive, to see if it's showing any errors.  Just run smartctl -h to see how to use it.

---

### Post by pirattrev on 2009-04-09
thank you for the suggestion. there are definitely bad sectors on the drive, a bunch. During the badblocks test my computer starting running into the I/O error flood when it started scanning the bad ones. What do I do now though? Should I buy a new harddrive? or is there a way to remove the problem of the badsectors by blacklisting them?

---

### Post by pirattrev on 2009-04-09
Bump

Does anyone know the commands or precedure to properly blacklist the badsectors on a drive? I had /dev/sda divided into /dev/sda1 for /, and /dev/sda5 for /home

---

### Post by lykwydchykyn on 2009-04-09
I'm pretty sure running fsck -c will do this, but you have to run in offline (e.g. --from a liveCD) because the disk needs to be unmounted.

Honestly, though, I would replace that disk straight off and throw it away.  A disk with loads of bad sectors is failing and will probably get steadily worse.

---

