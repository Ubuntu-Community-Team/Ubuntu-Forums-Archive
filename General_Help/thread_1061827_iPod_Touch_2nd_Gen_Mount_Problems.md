---
title: "iPod Touch 2nd Gen Mount Problems"
date: 2009-02-06
forum: General Help
---

### Post by nunyez on 2009-02-06
When I plug my ipod touch 2nd gen in, it mounts and unmounts rapidly along with giving two errors each time. The dialog title is Apple Ipod, Inc. I think

1) DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
2) Error initializing camera: -53: Could not claim the USB device

As you may or may not know new ipods do not mount as mass storage devices, if photos are present it will allow mounting as a camera to view only those photos. I've found the 2nd error common with cameras people have tried to mount, but different circumstances.

I have tried several different USB ports giving my pc the benefit of the doubt, all with the same result. My ipod is jailbroken (did these before jb also).

---

### Post by nunyez on 2009-02-06
Anyone?

---

### Post by mathewd on 2010-02-03
i have possibly a similar problem with a cell phone i'm connecting via usb data cable.
the phone (which should, and does, mount as a drive on windows and mac) seems to mount/unmount rapidly forever.

 "sudo fdisk -l" reveals the following information:

Disk /dev/mmcblk2: 2032 MB, 2032664576 bytes
64 heads, 63 sectors/track, 984 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk2p1               1         984     1983619+   6  FAT16

perhaps the Disk Identifier number is the cause? does yours yield a similar result? i really dont know how to fix this, so im hoping that if our problems are similar, someone else might be able to help us both ^_^

---

