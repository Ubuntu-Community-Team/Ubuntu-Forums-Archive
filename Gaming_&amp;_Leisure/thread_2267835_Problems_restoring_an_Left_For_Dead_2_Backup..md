---
title: "Problems restoring an Left For Dead 2 Backup."
date: 2015-03-04
forum: Gaming &amp; Leisure
---

### Post by mandarpowale on 2015-03-04
Hi

Please read the entire query in details

My system specifications are as follows
================================
Amd Athlon II X2 260 3.2 GHZ
Asus M4N68-T LE-V2
4GB DDR III 1333MHZ GSKILL RAM
ASUS HD7750 1GD5 V2
1 TB WD PURPLE
500 GB WD GREEN
(C: WINDOWS 7 SP1 250 GB , E: UBUNTU 234GB '/', 16 GB 'SWAP', F:463 GB) FROM 1TB
(D: 146 GB BAD SECTORS G: 146 GB GOOD, H: 172GB GOOD) FROM 500 GB HDD 
=================================================================

I am running steam successfully on a hdd partitioned for UBUNTU Linux 14.04 LTS

My linux is set to dual boot with Win7SP1 X64 ULT (which is installed first)

I applied all the updates to my 14.04.2 as auto requested by the Linux. I  copied all the compressed backups of my steam games (which I took using  steams backup and restore function in Win 7 SP1 64 bit) to default  steam's backup folder in UBUNTU  (/home/mandarpowale/.local/share/Steam/Backups).   When I try to restore l4d2 it hangs at 7.2GB done saying 'writing to  disk' , I have tried to give all the necessary info as possible  from my end. If you need any more info i'll be glad to give it to you.

Please suggest a solution ASAP

Thanking you for your time to read the long description,

Mandar D Powale

---

### Post by R33D3M33R on 2015-03-04
Is the HDD doing anything (LED blinking, you hear it working, etc.)? It might be converting the old game format to steam pipe which can take a long time.

---

### Post by mandarpowale on 2015-03-04
Hi, Good News is that Left 4 Dead 2 finally got installed. But it took a long long time. I want to create a data partition on one of my HDD. Please advise on how to do so. I want to use this partition to store the backup of my Steam Games.

---

### Post by mandarpowale on 2015-03-04
> **R33D3M33R said:**
> Is the HDD doing anything (LED blinking, you hear it working, etc.)? It might be converting the old game format to steam pipe which can take a long time.

It is good to hear that old game format( perhaps your mean NTFS format)  can be converted and Yes, the HDD LED was glowing all the time, system did not become unresponsive though. I feared for my HDD zapping out on me.

---

### Post by R33D3M33R on 2015-03-04
Actually, I was talking about this: [https://support.steampowered.com/kb_article.php?ref=7388-QPFN-2491](https://support.steampowered.com/kb_article.php?ref=7388-QPFN-2491)

---

### Post by mandarpowale on 2015-03-04
Can I store my downloaded files on an NTFS partition without loss of integrity since I hear ext4 is more advanced than NTFS? And How do I format an NTFS partition into EXT4 journalling ?

---

### Post by R33D3M33R on 2015-03-04
To convert partitions use GParted. Move data off the partition, format it and then move data back. **Be careful!**

---

