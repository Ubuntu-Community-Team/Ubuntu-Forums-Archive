---
title: "testdisk - Bad ending cylinder (CHS and LBA don't match)"
date: 2009-03-30
forum: General Help
---

### Post by moddie666 on 2009-03-30
Hello.

I realize there is another thread about this in existence already but the Information Presented There is less than usable. I will try to give you as much info as possible to make helping easier.

when testdisk analyzes the disk i get the following:

#########################################################################
Disk /dev/hdc - 80 GB / 74 GiB - CHS 155061 16 63
Current partition structure:
     Partition                  Start        End    Size in sectors
 1 * Linux                    0   1  1   159   5 63     160587

Warning: Bad ending head (CHS and LBA don't match)
 2 P Linux Swap             159   6  1  3155   9 63    3020220

Warning: Bad ending head (CHS and LBA don't match)
 3 P Linux                 3155  10  1 23459  15 63   20466810

Warning: Bad ending head (CHS and LBA don't match)
 4 P Linux                23460   0  1 155055  14 63  132648705

Warning: Bad starting head (CHS and LBA don't match)
##########################################################################

The search for backup superblocks on hdc3 or 4 remains without any result.

e2fsck tells me (sorry its in german):
##########################################################################
e2fsck 1.40-WIP (14-Nov-2006)
Konnte den ext2-Superblock nicht finden, versuche Backup-Blöcke...
e2fsck: Bad magic number in super-block beim Versuch, /dev/hdc4 zu öffnen

SuperBlock ist unlesbar bzw. beschreibt kein gültiges ext2
Dateisystem.  Wenn Gerät gültig ist und ein ext2
Dateisystem (kein swap oder ufs usw.) enthält,  dann ist der SuperBlock
beschädigt, und sie könnten e2fsck mit einem anderen SuperBlock:
    e2fsck -b 8193 <Gerät>
##########################################################################

the disk is rather old, so that might be a problem, but hdc1 works without incident, and hdc3 can also be mounted. On trying to mount hdc4 however it tells me it is unable to read the superblock.

Is there any hope of getting to the data on hdc4 or is it lost?

Any and all information would be greatly appreciated.
(btw my native language is german but i am very comfortable with english aswell)

greetings
/moddie

---

