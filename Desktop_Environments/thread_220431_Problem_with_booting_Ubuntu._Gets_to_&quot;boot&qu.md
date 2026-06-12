---
title: "Problem with booting Ubuntu. Gets to &quot;boot&quot; and freezes"
date: 2006-07-21
forum: Desktop Environments
---

### Post by microchip13 on 2006-07-21
I'm trying to install Ubuntu on a Pentium 4 with about a gig of RAM I believe on a 250GB Maxtor Drive.

The Install process was successful, however I cannot boot into Ubuntu.
When I try to boot it:

Booting 'Ubuntu,kernel 2.6.15-23-386'

root (hd0,0)
Filesystem type is ext2fs, partition type 0x83
kernel /boot/vmlinux-2.6.15-23-386 root=/dev/hda1 ro quiet splash
   [Linux-bzImage. setup =0x1c00, size = 0x15774d]
initrd /boot/initrd.img-2.6.15-23-386
   [Linux-initrd @ 0x1f942000, 0x6ad37b bytes]
savedefault
boot


And it just hangs here. I really need to get this working.

Any suggestions? I've tried several reinstalls and I still get the same problem.

---

### Post by kingmonkey on 2006-07-21
Does a LiveCD work?
Can you boot into recovery mode?

Might be something in your BIOS which is preventing it.

---

### Post by microchip13 on 2006-07-21
Live CD works, thats how I installed it.

REcovery mode seems to have the same problem.

---

