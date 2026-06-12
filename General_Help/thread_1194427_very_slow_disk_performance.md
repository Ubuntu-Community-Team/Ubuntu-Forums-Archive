---
title: "very slow disk performance"
date: 2009-06-22
forum: General Help
---

### Post by poisonborz on 2009-06-22
Hola,

I've recently installed Ubuntu on my sister's computer, and even while it's a quite capable computer (1.6G cpu, 512 ram) everything was awfully slow. More precisely, the hdd speed is awful, as one can see below:

```
hdparm -tT /dev/sda1

/dev/sda1:
 Timing cached reads:   178 MB in  2.00 seconds =  88.90 MB/sec
 Timing buffered disk reads:   10 MB in  3.57 seconds =   2.80 MB/sec
```

I also got esata errors on the start, and the boot is also very-very slow:

```
[28990.792050] ata1.00: exception Emask 0x0 SAct 0xff SErr 0x0 action 0x6 frozen
[28990.792065] ata1.00: cmd 60/80:00:00:4f:ae/00:00:07:00:00/40 tag 0 ncq 65536 in
[28990.792068] res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[28990.792073] ata1.00: status: { DRDY }
```

Even the LiveCD boots like this, so I guess there is something wrong with the handling of my motherboard ata... (regardless of hdd-s)
I've already tried to edit **/etc/initramfs-tools/modules** to blacklist drivers, but no luck...

I know I should try other distros to find out if this is really ubuntu's fault, but right now I'm stuck with a gutsy livecd. Any guess how I could fix this?
Thanks

---

