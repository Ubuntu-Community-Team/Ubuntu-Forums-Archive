---
title: "Not able to mount volume"
date: 2009-04-17
forum: General Help
---

### Post by dE_logics on 2009-04-17
I tried to share certain partition (after mounting them), to do so I went to /media and shared the mounted partitions.

Now after a reboot, 2 partitions are not getting mounted and giving me the following - 
[code]
mount:wrong fs type, bad option, bad superblock on /dev/sda10, missing codepage or helper program, or other error
In  some case useful info in found in syslog - try[code]



I'm absolutely pissed trying to 'mount' volumes in linux, it needs an excuse not to get mounted.

---

### Post by DJonsson2008 on 2009-04-17
are the partitions formated?

what file system?

what does gparted tell you about the partitions?

i believe gparted is available on ubuntu under admininstration>partition manager so something like that.
for ext partitions work between nautilus and konqueror.
also try nautilus and konqueror as root.

gparted can also be run from the command line.

for ntfs partitions install and use the
handy gui ntfs-config

also perhaps search for gui mount wrapper you find
gui's give you leverage, but gparted may well be your
first gui point of reference and status of the partitions
in question.

---

### Post by danwood76 on 2009-04-17
How are you mounting the drives?
Are they fixed partitions and what filesystems are they?

And are you sharing to windows PC's through samba?

If you mount a drive in linux for it to be mounted on every boot you need to add it to the /etc/fstab file.

---

### Post by dE_logics on 2009-04-17
> **DJonsson2008]are the partitions formated?

what file system?

what does gparted tell you about the partitions?[/quote]

JFS said:**
> How are you mounting the drives?
Are they fixed partitions and what filesystems are they?

Fixed partitions, JFS.

Right click>mount.

> And are you sharing to windows PC's through samba?

:lol: that's a later on problem, gotta work on this one first.

Currently its not getting mounted at all......forget editing fstab.

---

### Post by codeseer on 2009-04-17
```

blkid

sudo fdisk -l

```

---

### Post by dE_logics on 2009-04-18
blkid - 
```
/dev/sda5: UUID="3b2a85a4-3765-4908-b56f-e57a79ca5659" TYPE="jfs" 
/dev/sda6: UUID="e4e672d9-00da-431d-8686-1164d96d9b15" TYPE="reiserfs" 
/dev/sda7: UUID="1306394c-8c2c-41ed-aecc-02e0af6ed5c4" TYPE="swap" 
/dev/sda8: UUID="1C4EA04B2690ED08" LABEL="Broken Windows" TYPE="ntfs" 
/dev/sda9: LABEL="Media" UUID="a5a304aa-8804-4e77-82c6-38e6b8c8bca7" TYPE="jfs" 
/dev/sda10: LABEL="Game 1" UUID="5bdd7442-d35d-461b-ab71-b33434642dae" TYPE="jfs" 
/dev/sda11: LABEL="Game 2" UUID="7057fb45-5c3f-4a53-b43e-7ab4b0b9dec2" TYPE="jfs" 
/dev/sda12: UUID="3ccc8ce7-fd39-4f48-9731-0a0ca4722cd8" LABEL="My Documents" TYPE="reiserfs" 
/dev/sda13: LABEL="Write it!" UUID="695c8483-5797-4a5a-bf5e-9e462a6a8489" TYPE="jfs" 
/dev/loop0: TYPE="squashfs" 
```
fdisk -l
```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003dc24

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          14      112423+   7  HPFS/NTFS
/dev/sda2              15        9729    78035737+   5  Extended
/dev/sda5              15         906     7164958+  83  Linux
/dev/sda6             907        1441     4297356   83  Linux
/dev/sda7            1442        1823     3068383+  82  Linux swap / Solaris
/dev/sda8            1824        2103     2249068+   7  HPFS/NTFS
/dev/sda9            2104        5991    31230328+  83  Linux
/dev/sda10           5992        6947     7679038+  83  Linux
/dev/sda11           6948        7903     7679038+  83  Linux
/dev/sda12           7904        8285     3068383+  83  Linux
/dev/sda13           8286        9729    11598898+  83  Linux

```

---

### Post by codeseer on 2009-04-18
```

lsmod | grep jfs

```

---

### Post by dE_logics on 2009-04-18
It says - 
```

jfs                   199248  2 

```

---

### Post by codeseer on 2009-04-18
What's the mount command you're using?

---

### Post by NightwishFan on 2009-04-18
Replace /dev/sda with the name of your drive.

If you told it to mount on boot or it already has a designated mount point, please ignore below.

If not then do this;

```
sudo mkdir /media/mydrive
sudo mount /dev/sda /media/mydrive
```

If there is an error please tell us here.

If you worry about the disk, check it with jfs tools.

---

### Post by codeseer on 2009-04-18
> **NightwishFan said:**
> Replace /dev/sda with the name of your drive.

If you told it to mount on boot or it already has a designated mount point, please ignore below.

If not then do this;

```
sudo mkdir /media/mydrive
sudo mount /dev/sda /media/mydrive
```

If there is an error please tell us here.

If you worry about the disk, check it with jfs tools.

Would you agree with:

```

sudo mount -v -t jfs -o rw,users,noexec,nosuid,nodev /dev/sda10 /mnt/game-1

```

I thought jfs was still pretty unusable.

---

### Post by NightwishFan on 2009-04-18
Is there an error?

Also do you have permissions to view files? That is a lame question as you seem to know what you are doing.

---

### Post by codeseer on 2009-04-18
This is what he got:

```

mount:wrong fs type, bad option, bad superblock on /dev/sda10, missing codepage or helper program, or other error
In some case useful info in found in syslog - try

```

He also said '2 partitions', so I just assume he's trying to mount the two game partitions.

---

### Post by NightwishFan on 2009-04-18
> **codeseer said:**
> This is what he got:

```

mount:wrong fs type, bad option, bad superblock on /dev/sda10, missing codepage or helper program, or other error
In some case useful info in found in syslog - try

```

He also said '2 partitions', so I just assume he's trying to mount the two game partitions.

Did you run a filesystem check on any of those? If not, do so.

---

### Post by dE_logics on 2009-04-18
Ok...the problem was with windows; I made the partitions before installing windows, and while doing that (since it modifies the MFT and partition tables) it ruptures information about the non MS file systems.

---

### Post by dE_logics on 2009-04-19
Ok problems back...with the same partitions.

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
Great...it says 'solved'...guess I gotta start a new thread.

---

