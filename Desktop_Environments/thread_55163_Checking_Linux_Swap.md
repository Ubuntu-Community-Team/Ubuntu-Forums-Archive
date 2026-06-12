---
title: "Checking Linux Swap"
date: 2005-08-07
forum: Desktop Environments
---

### Post by SuperMike on 2005-08-07
I used to have RH9 and they had a defined swap partition. In those days when I asked about it, some people said that you could also implement a swap file instead of a swap partition. Now I have Ubuntu with 256MB and I noticed that once I open enough simultaenous apps up (that seventh app can sometimes be the killer), it starts churning the hard drive terribly and either just freezes everything up (including GNOME desktop) or shuts everything down.

So, I went looking for the Ubuntu swapfile or swap partition. I couldn't find it. Where is it? When I do "df --human-readable", I only find references to:

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              14G  2.2G   11G  17% /
tmpfs                 126M     0  126M   0% /dev/shm
/dev/hda2              24G  467M   23G   3% /home
/dev                   14G  2.2G   11G  17% /.dev
none                  5.0M  2.8M  2.3M  56% /dev

(Note, I created /home on a separate partition so that Linux upgrades have a chance to run more smoothly.)

Anyone know where Ubuntu put the swap space? And, can anyone tell me how I can check it to see if I'm having problems in its configuration that could explain my inability to have more than 6 (approx.) apps open at the same time?

P.S. Yes, as soon as my next paycheck comes in, I plan to go to crucial.com and get some RAM for my Dell PowerEdge 300SC Server. (I tried 2 times in vain with dell.com before and they botched it up 2 times in a row, shipping me the wrong ram!)

---

### Post by C38a7r1zvl on 2005-08-07
check your /etc/fstab to see which partition is used for swap space (the one with "swap" in its line, obviously) or try "cat /proc/swaps" and use "cat /proc/meminfo | grep  Swap" to see the usage of your swap space.

---

### Post by SuperMike on 2005-08-07
dePOLL,

This is what I have. It looks like somehow my Ubuntu is **botched** and I **don't** have a swapfile. Little wonder I have trouble when I try to open approx. more than 6 apps simultaneously.

root@host:/home/supermike # cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2       /home           ext3    defaults        0       2
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

root@host:/home/supermike # cat /proc/swaps

root@host:/home/supermike # cat /proc/meminfo | grep Swap
SwapCached:          0 kB
SwapTotal:           0 kB
SwapFree:            0 kB

So how do I fix this?

---

### Post by C38a7r1zvl on 2005-08-08
You have to create a new partition and then put
```
/dev/hdaX       none            swap    sw              0       0
```
in your /etc/fstab and type "sudo swapon /dev/hdaX" to enable it without rebooting. Post your partition table ("sudo apt-get install parted" - "parted /dev/hda" - "print" <- output of this command - "quit") if you want me to recommend a way to repartition your hdd.

---

