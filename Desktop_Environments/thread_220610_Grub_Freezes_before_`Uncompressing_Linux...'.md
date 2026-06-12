---
title: "Grub Freezes before `Uncompressing Linux...'"
date: 2006-07-21
forum: Desktop Environments
---

### Post by JoeyG on 2006-07-21
**Originally posted on **[LinuxQuestions.org](http://www.linuxquestions.org/questions/showthread.php?t=464619):

I installed Ubuntu 6.0.2 on a Athlon (now Sempron) 2000+ with 512Mb of RAM and four hard drives (15Gb, 20Gb, 1.2Gb, 1.2Gb). It worked fine, and my partition setup was as follows:

```

/dev/hda1 /boot 100Mb ext2
/dev/hda2 swap 1Gb    swap
/dev/hda3 /     10Gb ext3
/dev/hda4 /srv ~3.9Gb ext3

/dev/hdb1 /var 20Gb ext3

/dev/hdc1 md0 1.2Gb RAID1
/dev/hdd1 md0 1.2Gb RAID1

/dev/md0 /home 1.2Gb ext3

```

However, my dad soon wanted his computer back, so I had to move my hard drives up to my system, which has the following specs: Pentium 133, 128Mb RAM, 5 PCI/ISA ports (5 of each),
and a fairly old BIOS, which doesn't support drives over 8.5Gb. However, since my /boot partition is in the first 100Mb of the first drive, it shouldn't matter too much.

My heating system is fine; I put brand new quality thermal paste on the CPU and added a 120mm fan. I also ran memtest86 for 10 hours, and my memory is fine.

When booting up I get the following output:
```

Booting 'Ubuntu, kernel 2.6.15-23-server'

root (hd0, 0)
Filesystem type is ext2fs, partition type 0x83
kernel /vmlinuz-2.6.15-23-server root=/dev/hda3 ro quiet splash
[Linux-bzImage, setup=0x1c00, size=0x165b75f]
initrd /initrd.img-2.6.15-23-server
[Linux-initrd @ 0x79500000, 0x69f637 byes]
savedefault
boot

```

At that point it freezes, with no hard drive activity whatsoever. I've left it for about 30 minutes, and no change.

I tried removing `quiet' and `splash' from the kernel line, as well as adding `acpi=off pci=noacpi, noapic, nopcm, pcm=off' and various combinations of those options. No change.


I've spent several hours searching for a solution, but I can't seem to figure it out. I also had this problem with Fedora Core 5. It worked fine on my laptop, a Pentium II 366Mhz with 256Mb of RAM. However, that system had one 4.5Gb HD and that was it.

---

