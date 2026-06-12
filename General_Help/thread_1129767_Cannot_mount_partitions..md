---
title: "Cannot mount partitions."
date: 2009-04-19
forum: General Help
---

### Post by dE_logics on 2009-04-19
sda8 and sda9 are not getting mounted.

blkid - 

```

/dev/sda1: UUID="3B9FEEB10F622553" TYPE="ntfs" 
/dev/sda5: UUID="c279360b-ba1d-492a-9338-286af54c0cf0" TYPE="reiserfs" 
/dev/sda6: UUID="23b2a0aa-9d24-4418-8e39-abf246d4e997" TYPE="reiserfs" 
/dev/sda7: TYPE="swap" UUID="9df6447b-68c1-47b2-8f3b-3dc756d44dde" 
/dev/sda8: LABEL="game1" UUID="4e119755-d7fa-47b0-a537-9143fcfb49fd" TYPE="jfs" 
/dev/sda9: LABEL="game2" UUID="a4ef7022-9ebd-42b6-b964-ed90dbc0c895" TYPE="jfs" 
/dev/sda10: UUID="3fa509eb-fa08-4607-a284-18ae94cb4fe1" LABEL="mydocuments" TYPE="reiserfs" 
/dev/sda11: LABEL="media" UUID="b6a18f0b-9f45-4ba6-b2a2-c8fd14a9a914" TYPE="jfs" 
/dev/sda12: LABEL="writeit!" UUID="d4ea8c9a-e43f-45e4-997d-379391f61222" TYPE="jfs" 

```
fdisk -l
```

255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003dc24

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         293     2353491    7  HPFS/NTFS
/dev/sda2             294        9729    75794670    5  Extended
/dev/sda5             294        1185     7164958+  83  Linux
/dev/sda6            1186        1720     4297356   83  Linux
/dev/sda7            1721        2102     3068383+  82  Linux swap / Solaris
/dev/sda8            2103        3058     7679038+  83  Linux
/dev/sda9            3059        4014     7679038+  83  Linux
/dev/sda10           4015        4422     3277228+  83  Linux
/dev/sda11           4423        8310    31230328+  83  Linux
/dev/sda12           8311        9729    11398086   83  Linux

```

How do I check for problems?

fsck -t jfs /dev/sdaX

right?

it says fsck.jfs does not exist.

---

### Post by dE_logics on 2009-04-19
Installed utility jfs_fsck...problem solved.

---

