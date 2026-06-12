---
title: "[SOLVED] Increased partition doesn't show up as having increased"
date: 2009-01-01
forum: General Help
---

### Post by RPG Master on 2009-01-01
So I just decreased my Vista partition and increased my Ubuntu partition. It was 97GB, now it should be 105GB... If I check partition editor in Ubuntu it shows 105GB, but when I check Disk Usage Analyzer it shows up as still being 97GB.

And when I was doing the repartitioning on a Linux Mint LiveCD, it gave me an error when it got to "Check and Repair".

---

### Post by taurus on 2009-01-01
What are the outputs of these commands from a terminal?

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by RPG Master on 2009-01-01
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x33b666e8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4079    32764536    7  HPFS/NTFS
/dev/sda2           17917       19457    12378082+   7  HPFS/NTFS
/dev/sda3            4080       17855   110655720   83  Linux
/dev/sda4           17856       17916      489982+  82  Linux swap / Solaris

```

---

### Post by RPG Master on 2009-01-02
Bump

---

### Post by RPG Master on 2009-01-03
Bump... again.

Come on people, help! :confused:

---

### Post by Polygon on 2009-01-03
use gparted and tell it to check and repair the partiton in question (right click > check   i think), if all goes well it should fix it up

---

### Post by RPG Master on 2009-01-03
But I tried that after it gave me the error. Then it gave me another error :(

---

### Post by Slim Odds on 2009-01-03
> **RPG Master said:**
> But I tried that after it gave me the error. Then it gave me another error :(

An error, an error, an error.....

That's not the kind of detailed description that going to get you an answer (not matter how many times you "bump").

What was the error?

Your Windows partition probably has errors (that need to be fixed in Windows).

---

### Post by RPG Master on 2009-01-03
Took a screen shot of the error.

---

### Post by Slim Odds on 2009-01-03
> **RPG Master said:**
> Took a screen shot of the error.

The second error message suggests running:```
e2fsck -f /dev/sda3
```Did you?

---

### Post by RPG Master on 2009-01-03
OK, I tried it again (I had tried it while still using the Mint LiveCD and it gave me an error).

```
/dev/sda3: recovering journal
Clearing orphaned inode 705003 (uid=1000, gid=1000, mode=0100644, size=842)
Clearing orphaned inode 4522491 (uid=1000, gid=1000, mode=0100600, size=2048)
Clearing orphaned inode 4522421 (uid=1000, gid=1000, mode=0100600, size=2056)
Clearing orphaned inode 4522360 (uid=1000, gid=1000, mode=0100600, size=2576)
Clearing orphaned inode 1450005 (uid=1000, gid=1000, mode=0100644, size=32912)
Clearing orphaned inode 3572917 (uid=1000, gid=1000, mode=0100644, size=28200)
Clearing orphaned inode 3572910 (uid=1000, gid=1000, mode=0100644, size=39564)
Clearing orphaned inode 3572907 (uid=1000, gid=1000, mode=0100644, size=31581)
Clearing orphaned inode 3572891 (uid=1000, gid=1000, mode=0100644, size=57278)
Clearing orphaned inode 3572655 (uid=1000, gid=1000, mode=0100644, size=31322102)
Clearing orphaned inode 1450026 (uid=1000, gid=1000, mode=0100644, size=38658)
Clearing orphaned inode 1450028 (uid=1000, gid=1000, mode=0100644, size=42863)
Clearing orphaned inode 1449993 (uid=1000, gid=1000, mode=0100644, size=34281)
Clearing orphaned inode 1450022 (uid=1000, gid=1000, mode=0100644, size=843)
Clearing orphaned inode 1450021 (uid=1000, gid=1000, mode=0100644, size=3096)
Clearing orphaned inode 1318950 (uid=1000, gid=1000, mode=0100644, size=2653)
Clearing orphaned inode 3572909 (uid=1000, gid=1000, mode=0100644, size=2653)
Clearing orphaned inode 3572908 (uid=1000, gid=1000, mode=0100644, size=2475)
Clearing orphaned inode 3572912 (uid=1000, gid=1000, mode=0100644, size=771683)
Clearing orphaned inode 4522106 (uid=1000, gid=1000, mode=0100600, size=28700)
Pass 1: Checking inodes, blocks, and sizes
Deleted inode 4522106 has zero dtime.  Fix<y>? 
```

Should I Fix it, or is their some risk of losing data?

---

### Post by RPG Master on 2009-01-03
So I hit "Y" to everything it ask.

:(

I rebooted my computer. After the "HP" logo the screen blacked out and went back to the HP logo. And it just repeats it over and over...

So I am now typing this on my Mint LiveCD. I am trying to "Check" my Ubuntu partition with Gparted.

---

### Post by RPG Master on 2009-01-03
Well the check didn't fix anything. Dose it have something to do with Grub? Can I fix it with an Ubuntu LiveCD?

I am filling really desperate now :(

---

