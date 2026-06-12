---
title: "HDD Freezing - SATA Soft Resetting Link"
date: 2009-04-04
forum: General Help
---

### Post by RemyLeBeau on 2009-04-04
Hi this is my first time posting here and the reason is that I have the following problem:

One of my HDD freezes after some time working, especially if it's under medium of heavy load: it needs some time
before errors start to show up. I'm currently victim of the infamous "soft resetting link" thing.

It's annoying since sometimes nothing noticeable happens but under heavy load makes the S.O. almost unusable and the worst thing that happened
was that a complete hung-up which forced me to do a hard-reset which ended in a malfunctioning ubuntu. 

Here's an extract of the attached syslog.txt

Apr  2 15:10:24 Cyberdine kernel: [13164.937047] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Apr  2 15:10:24 Cyberdine kernel: [13164.937058] ata3.00: cmd 35/00:08:47:19:e2/00:00:1c:00:00/e0 tag 0 dma 4096 out
Apr  2 15:10:24 Cyberdine kernel: [13164.937060]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Apr  2 15:10:24 Cyberdine kernel: [13164.937063] ata3.00: status: { DRDY }
Apr  2 15:10:24 Cyberdine kernel: [13164.937073] ata3: soft resetting link
Apr  2 15:10:25 Cyberdine kernel: [13165.130110] ata3.00: configured for UDMA/133
Apr  2 15:10:25 Cyberdine kernel: [13165.130127] ata3: EH complete
Apr  2 15:10:25 Cyberdine kernel: [13165.130846] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Apr  2 15:10:25 Cyberdine kernel: [13165.131131] sd 2:0:0:0: [sda] Write Protect is off
Apr  2 15:10:25 Cyberdine kernel: [13165.131135] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr  2 15:10:25 Cyberdine kernel: [13165.135444] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  2 15:11:03 Cyberdine kernel: [13203.961033] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Apr  2 15:11:03 Cyberdine kernel: [13203.961044] ata3.00: cmd 35/00:10:d7:6d:53/00:00:1c:00:00/e0 tag 0 dma 8192 out
Apr  2 15:11:03 Cyberdine kernel: [13203.961046]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Apr  2 15:11:03 Cyberdine kernel: [13203.961049] ata3.00: status: { DRDY }

(...)


I've also attached lsmod, version, and lspci-v for more details about the hardware I'm using. 

CPU Config is a Athlon x2 4400+, 2Gib Ram, Asus m2v motherboard (via chipset) and linux is installed like this (I have to HDDs SATA)
*sda1 (WD 250): sda1: Lenny - sda2(sda5): swap - sda3: (Data, also ext3) - sda4: Ubuntu 8.10 i386
*sdab (WD 160): sdb1: Data - sdb2: WinXP

The reason why I'm posting this is that I've seen similiar bugs to this one but none of them was aparently solved.

Moreover it has not only ocurred in ubuntu 8.10 (i386) from which all the logfiles come from but also in the amd64 release.

Doing some research found out that it could be an ubuntu-related issue (kernel-level) so I switched to Debian Lenny 5 and guess what? Happened here too.

Some people reported that this was a kernel-level issue with some via-chipsets, more specifically that newer linux kernels were not supporting crappy chipsets like mine.

Something interesting is that sda3 has been mounted like 120 without being checked and now a fsck -n on /dev/sda3 found some errors maybe due to normal usage or to those nasty hard-resets mentioned before.


I would appreciate any response!

Thanks!

---

