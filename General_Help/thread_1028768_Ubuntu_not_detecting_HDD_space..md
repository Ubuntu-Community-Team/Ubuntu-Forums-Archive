---
title: "Ubuntu not detecting HDD space."
date: 2009-01-02
forum: General Help
---

### Post by Praseodymi on 2009-01-02
I recently notice that at the corner of the file browser window it said I only had about 500mb of space left, so I cleaned out the Wastebasket and looked again. It now said I had about 4gb of space. I thought this was odd as I had made a 100gb partition for Ubuntu (8.10) and I couldn't possibly have used it all. When I went into gparted to resize the partition it said that there was still about 85gb of space left, although ubuntu still stops me from going over this imaginary 20gb limit. How can I increase the amount of actual *usable* space?

EDIT: Whoops! I posted this twice! :S

---

### Post by nemilar on 2009-01-02
Can you post the output of the following commands:

```
df -h 
```

```
sudo /sbin/fdisk -l
```

---

### Post by Praseodymi on 2009-01-02
Sure

```
Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                       13G  8.7G  3.5G  72% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  212K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  2.8M  1.5G   1% /dev
tmpfs                 1.5G  696K  1.5G   1% /dev/shm
/dev/sdb3             101G   15G   86G  15% /host
lrm                   1.5G  2.0M  1.5G   1% /lib/modules/2.6.27-9-generic/volatile
/dev/scd0             4.2G  4.2G     0 100% /media/Oblivion GOTY 1

```

```
Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd282d282

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4997    40138371    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x96ab1ba3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4997    40138371    7  HPFS/NTFS
/dev/sdb2            4998       47679   342843165    7  HPFS/NTFS
/dev/sdb3           47680       60801   105402465    7  HPFS/NTFS

```

Here BTW, sdb1 is there for a reason, it's a long story, ad it has some windows stuff on. sdb2 is the bigger windows one, and sdb3 is the one I made for Ubuntu.

---

### Post by dcstar on 2009-01-02
> **nemilar said:**
> Can you post the output of the following commands:

```
df -h 
```


"df -h" is useless for seeing file space that root has used, this will show ALL used space:

```
sudo df -h
```

---

### Post by nemilar on 2009-01-02
> **dcstar said:**
> "df -h" is useless for seeing file space that root has used, this will show ALL used space:

```
sudo df -h
```

I wasn't aware of this.... in fact I'm not sure you are correct (not saying you aren't).  'df' and 'sudo df' give me the same readings on all systems I have [root] access to....  are you thinking of du, perhaps?  I'm interested to learn more.

---

### Post by nemilar on 2009-01-02
Looks like you have 85GB free in /host.  Is this the partition you were thinking of?

---

### Post by Praseodymi on 2009-01-02
Oh lord, now I feel like an idiot. Yeah, that seems thats where all the space is. Is there anyway to remedy this? To put the space somewhere more useful?

---

### Post by nemilar on 2009-01-02
To clarify, are you using Wubi?  Your partitioning schema looked strange to me, and some googling suggests that...  

In which case I might ask someone else, I have never used Wubi before...:confused::confused::confused:

---

### Post by Praseodymi on 2009-01-02
Yes, when I tried to install Ubuntu from the CD it was corrupt, and when I went back into Windows to fix it I saw that it could be installed from there, so I went with the easy option.

---

### Post by nemilar on 2009-01-03
Bump....
Not really sure what to do here, as it's a Wubi environment.  Hopefully someone else can solve this thread?

---

