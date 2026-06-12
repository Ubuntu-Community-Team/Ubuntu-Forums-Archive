---
title: "hard disk problem: bad superblock/group descriptors corrupted"
date: 2008-12-12
forum: General Help
---

### Post by jcmag on 2008-12-12
I've an USB external hard drive that I can't mount anymore. I've the following error:
```
jc@jc-laptop:~$ dmesg | tail
[  994.739118] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[  994.739844] sd 2:0:0:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)
[  994.740606] sd 2:0:0:0: [sdc] Write Protect is off
[  994.740610] sd 2:0:0:0: [sdc] Mode Sense: 00 38 00 00
[  994.740613] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[  994.740619]  sdc: sdc1
[  994.772810] sd 2:0:0:0: [sdc] Attached SCSI disk
[  994.773151] sd 2:0:0:0: Attached scsi generic sg2 type 0
[COLOR="Red"][  995.199847] EXT3-fs error (device sdc1): ext3_check_descriptors: Inode table for group 912 not in group (block 0)!
[  995.200606] EXT3-fs: group descriptors corrupted![/COLOR]

```

e2fsck told me the superblock was bad ; after searching on the web I did the following: 

```
sudo e2fsck -y -v -b 71663616 /dev/sdc1
```

using all superblocks given by:

```
jc@jc-laptop:~$ sudo mke2fs -n /dev/sdc1
mke2fs 1.41.3 (12-Oct-2008)
Étiquette de système de fichiers=
Type de système d'exploitation*: Linux
Taille de bloc=4096 (log=2)
Taille de fragment=4096 (log=2)
30531584 i-noeuds, 122096000 blocs
6104800 blocs (5.00%) réservés pour le super utilisateur
Premier bloc de données=0
Nombre maximum de blocs du système de fichiers=0
3727 groupes de blocs
32768 blocs par groupe, 32768 fragments par groupe
8192 i-noeuds par groupe
Superblocs de secours stockés sur les blocs*: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
	102400000

```

But I always have the same error. What could I do now?

---

### Post by caljohnsmith on 2008-12-12
You might have to resort to using some program like [photorec]("http://www.cgsecurity.org/wiki/PhotoRec") to recover your files off the HDD, and then reformat the partition. I would run a HDD diagnostic test on that drive though to make sure it isn't having hardware problems. If you would like help running a "SMART" HDD diagnostic test on the drive from the Ubuntu command line, let me know and I can give you specific directions if you want. Good luck and let me know how it goes.

---

### Post by jcmag on 2008-12-14
I'd prefer to try to fix the problems because recovery tools don't recover .vmdk files (vmware virtual machines) and they lose the folder hierarchy, as my hard disk is a backup disk these two features are very important to me.

I think I tried to do SMART test but I don't remember exactly what I did, do you have specific commands to try ?

---

### Post by caljohnsmith on 2008-12-14
OK, to run a SMART HDD test, first open a terminal and do:
```
sudo apt-get install smartmontools
```
First do the following to save the current health status parameters of your HDD to a file on your desktop:
```
sudo smartctl -a /dev/sdc > ~/Desktop/sdc_health_before_test.txt
```
Then run:
```
sudo smartctl -t long /dev/sdc
```
That command will immediately terminate while the HDD begins its self-test, and it could take quite a while. You can monitor the progress with:
```
sudo smartctl -a /dev/sdc | grep -A 1 -i "self-test execution status"
```
Once the above command says the test is done, then do:
```
sudo smartctl -a /dev/sdc > ~/Desktop/sdc_health_after_test.txt
sudo smartctl -H /dev/sdc
```
And please post the contents of the two files on your desktop so I can see the results.

---

### Post by jcmag on 2008-12-14
My hard disk doesn't seem to support SMART, maybe because it's an USB external hard disk?

```
jc@jc-laptop:~$ sudo smartctl -a /dev/sdc
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

Device: SAMSUNG  HD501LJ          Version: 0-10
Device type: disk
Local Time is: Sun Dec 14 20:00:10 2008 CET
Device does not support SMART

Error Counter logging not supported
Device does not support Self Test logging

```

---

### Post by caljohnsmith on 2008-12-14
It looks like you are probably right about the drive not supporting a SMART test, but you could try each of the following and see if it gets you any further:
```
sudo smartctl -F samsung -a /dev/sdc
sudo smartctl -F samsung2 -a /dev/sdc
sudo smartctl -F samsung3 -a /dev/sdc
```
Let me know what those return.

---

### Post by jcmag on 2008-12-14
Same message as above, for the three commands  :(

---

### Post by caljohnsmith on 2008-12-14
I think you would have to visit Samsung's website, because they most likely have their own software for testing that particular model you have. Good luck though, sorry I can't help out any more than that.

---

### Post by jcmag on 2008-12-14
ok, thanks for you help

---

