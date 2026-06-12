---
title: "Total freeze, npviewer.bin"
date: 2009-03-27
forum: General Help
---

### Post by Zer0d on 2009-03-27
It seems like the problem occurs when I'm using deluge bit-torrent client, the computer goes into a total freeze even CTRL + ALT + BACKSPACE doesn't manage to restart Gnome. I'm running Ubuntu 8.10 x64.

In the syslog this is what happened right before the freeze:

```

Mar 27 21:31:36 ***** kernel: [  698.872541] npviewer.bin[7247]: segfault at 0 ip 0000000000000000 sp 00000000ffd5e99c error 14 in npviewer.bin[8048000+1a000]

```

Could npviewer.bin actually cause the total freeze of my computer?

---

### Post by Zer0d on 2009-03-27
I did a **e2fsck /dev/sda1** on the drive the bit-torrent client was downloading to when the freeze happened. Could bad sectors/blocks be the cause of the problem?

Here is the output of e2fsck:
```

/media/disk was not cleanly unmounted, check forced.
Pass 1: Checking inodes, blocks, and sizes
Inode 860196, i_blocks is 668776, should be 676328.  Fix<y>? yes

Inode 860184, i_blocks is 636480, should be 636512.  Fix<y>? yes

Deleted inode 1433601 has zero dtime.  Fix<y>? yes

Pass 2: Checking directory structure
Entry '*****' in /.Trash-1000/files/***** (868376) has deleted/unused inode 868381.  Clear<y>? yes

Pass 3: Checking directory connectivity
Pass 3A: Optimizing directories
Pass 4: Checking reference counts
Unattached inode 860347
Connect to /lost+found<y>? yes

WARNING: PROGRAMMING BUG IN E2FSCK!
	OR SOME BONEHEAD (YOU) IS CHECKING A MOUNTED (LIVE) FILESYSTEM.
inode_link_info[860347] is 65500, inode.i_links_count is 65535.  They should be the same!
Inode 860347 ref count is 65535, should be 1.  Fix<y>? yes

Pass 5: Checking group summary information
Block bitmap differences:  -(3842386--3842412) -(4402623--4402726) -(4852410--4852477) -(4852688--4852757) -(4853152--4853214) -(4853216--4853219) -(4853224--4853231) -(4855170--4855226) -(4855730--4855768) -(4855884--4855907) -(4855944--4855961) -5748736
Fix<y>? yes

Free blocks count wrong for group #117 (1784, counted=1811).
Fix<y>? yes

Free blocks count wrong for group #134 (2978, counted=3082).
Fix<y>? yes

Free blocks count wrong for group #175 (19, counted=20).
Fix<y>? yes

Free blocks count wrong (6388060, counted=6388192).
Fix<y>? yes

Inode bitmap differences:  -868381 -1433601
Fix<y>? yes

Free inodes count wrong for group #106 (8165, counted=8166).
Fix<y>? yes

Free inodes count wrong for group #175 (8171, counted=8172).
Fix<y>? yes

Directories count wrong for group #175 (5, counted=4).
Fix<y>? yes

Free inodes count wrong (12813218, counted=12813220).
Fix<y>? yes


/media/disk: ***** FILE SYSTEM WAS MODIFIED *****
/media/disk: 23644/12836864 files (5.5% non-contiguous), 44933450/51321642 blocks
root@zer0d-desktop:/var/log# e2fsck /dev/sda1
e2fsck 1.41.3 (12-Oct-2008)
/media/disk: clean, 23644/12836864 files, 44933450/51321642 blocks


```

---

### Post by Cyclops_ on 2009-05-19
I am getting frequent freeze ups as well.... though I'm not using the same software as mentioned.

Another interesting thing that happens is that instead of freezing up, Firefox will just randomly close.  If I immediately look at the message log (via dmesg), I see the same error as mentioned above (npviewer segfaulting) -- and I see it every time.

Any thoughts, anyone?

---

### Post by xzero1 on 2009-05-25
Same problem here with firefox.

```
 npviewer.bin[4187]: segfault at f55ad030 ip 00000000f78fa9e0 sp 00000000ffccb6dc error 4 in libpthread-2.9.so[f78f3000+15000]
```As for firefox this bug seems to be connected to flash. I will try disabling flash.

Edit:

Disabling flash does not work.

---

