---
title: "Second Hard Drive Problems"
date: 2006-06-03
forum: Desktop Environments
---

### Post by NeghVar on 2006-06-03
Ok everything was going fine until this morning. When I started up it normally mounts my second HD without any problems but today it decided it wouldn't anymore. So I went to Disks and tried to tell it to load from there but it wont, I changed the mount point and nothing seems to work? So is this just the case of my HD being punched or am I missing something?

---

### Post by kingmonkey on 2006-06-03
what error messages? /var/log/syslog

---

### Post by NeghVar on 2006-06-03
There are no real error messages there, this is what it shows for where it is mounting my drives though, hdb1 is missing:

> Jun  3 13:09:09 dapperdesktop kernel: [4294673.727000] Probing IDE interface ide0...
Jun  3 13:09:09 dapperdesktop kernel: [4294674.113000] hda: SAMSUNG SP0411N, ATA DISK drive
Jun  3 13:09:09 dapperdesktop kernel: [4294674.725000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Jun  3 13:09:09 dapperdesktop kernel: [4294674.735000] Probing IDE interface ide1...
Jun  3 13:09:09 dapperdesktop kernel: [4294675.529000] hdc: HL-DT-ST DVDRAM GSA-4163B, ATAPI CD/DVD-ROM drive
Jun  3 13:09:09 dapperdesktop kernel: [4294676.243000] hdd: HL-DT-ST GCE-8526B, ATAPI CD/DVD-ROM drive
Jun  3 13:09:09 dapperdesktop kernel: [4294676.295000] ide1 at 0x170-0x177,0x376 on irq 15
Jun  3 13:09:09 dapperdesktop kernel: [4294676.310000] hda: max request size: 1024KiB
Jun  3 13:09:09 dapperdesktop kernel: [4294676.329000] hda: 78242976 sectors (40060 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
Jun  3 13:09:09 dapperdesktop kernel: [4294676.332000] hda: cache flushes supported
Jun  3 13:09:09 dapperdesktop kernel: [4294676.332000]  hda: hda1 hda2
Jun  3 13:09:09 dapperdesktop kernel: [4294676.358000] hdc: ATAPI 63X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
Jun  3 13:09:09 dapperdesktop kernel: [4294676.358000] Uniform CD-ROM driver Revision: 3.20
Jun  3 13:09:09 dapperdesktop kernel: [4294676.374000] hdd: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
Jun  3 13:09:09 dapperdesktop kernel: [4294676.657000] usbcore: registered new driver usbfs
Jun  3 13:09:09 dapperdesktop kernel: [4294676.657000] usbcore: registered new driver hub
Jun  3 13:09:09 dapperdesktop kernel: [4294676.660000] USB Universal Host Controller Interface driver v2.3
Jun  3 13:09:09 dapperdesktop kernel: [4294676.661000] **** SET: Misaligned resource pointer: dfcb70e2 Type 07 Len 0

This comes up a bit later:

> Jun  3 13:09:09 dapperdesktop kernel: [4294677.172000] Attempting manual resume
Jun  3 13:09:09 dapperdesktop kernel: [4294677.188000] EXT3-fs: INFO: recovery required on readonly filesystem.
Jun  3 13:09:09 dapperdesktop kernel: [4294677.188000] EXT3-fs: write access will be enabled during recovery.
Jun  3 13:09:09 dapperdesktop kernel: [4294677.309000] EXT3-fs: recovery complete.
Jun  3 13:09:09 dapperdesktop kernel: [4294677.309000] kjournald starting.  Commit interval 5 seconds
Jun  3 13:09:09 dapperdesktop kernel: [4294677.309000] EXT3-fs: mounted filesystem with ordered data mode.

Further along I get the only real warning or error:

> Jun  3 13:10:46 dapperdesktop kernel: [4294819.651000] Warning: /proc/ide/hd?/settings interface is obsolete, and will be removed soon!

---

### Post by NeghVar on 2006-06-03
Ok, just so anyone wonders it seems to have been a loose cable to the HD, not really sure how as it was just working but it seems to be workin now. thanks anyways guys

---

