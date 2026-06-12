---
title: "Connecting and configuring NEUROS OSD on a PC"
date: 2009-04-05
forum: General Help
---

### Post by !nspiRatioN on 2009-04-05
I am currently using slackware 12.2 with kernal 2.6.I actually wana connect my Neuros OSD with my PC (Intel C2D) but unfortunately i coundn't find a way to connect and configure the device with the PC.

When i supply:

```
root@pieas:~# lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 003: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04d9:1603 Holtek Semiconductor, Inc.
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 04d9:0499 Holtek Semiconductor, Inc.
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

it detects the device but nothing happens as i can't see the device functioning.furthermore supplying the command dmesg |grep sd gives

```
root@pieas:~# dmesg |grep sd
Driver 'sd' needs updating - please use bus_type methods
sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
sd 2:0:0:0: [sda] Write Protect is off
sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
sd 2:0:0:0: [sda] Write Protect is off
sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
 sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 sda10 sda11 >
sd 2:0:0:0: [sda] Attached SCSI disk
EXT4-fs warning (device sda10): ext4_fill_super: extents feature not enabled on this filesystem, use tune2fs.
EXT4-fs: sda10: not marked OK to use with test code.
sd 2:0:0:0: Attached scsi generic sg0 type 0

```

I m very worried about this situation.can anyone help me to configure the device

Regards

-!nspiRatioN

---

