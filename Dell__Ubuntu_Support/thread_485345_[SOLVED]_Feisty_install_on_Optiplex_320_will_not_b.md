---
title: "[SOLVED] Feisty install on Optiplex 320 will not boot"
date: 2007-06-26
forum: Dell  Ubuntu Support
---

### Post by Co.Sinecure on 2007-06-26
**Update:**
The solution to this can be found [here]("http://ubuntuforums.org/showthread.php?p=2919008#post2919008")

-----
Hi All,

I just got a new work machine that i'm attempting to install feisty on as a dual boot with Windows XP (required for some specific software).

The end result of 2 attempts at installation was:
-GRUB loaded, with all OSs from both hard drives listed
-Selected the Ubuntu I was trying to boot (tried both normal and rescue mode)
-Screen came up with single cursor in top left, no other text. Did not do anything in the ~15mins or so I left it.
Could not type, switch terminals or anything.

---
Here is the process I've done so far:

I attempted to partition the drive with the 7.04 live DVD, but gparted crashed when I tried to make all the changes I wanted at one time. Once I split it up it handled each step ok. 
The resulting partition table is:
```

/dev/sda1    fat          31.35 MB       (Dell partition)
/dev/sda2    NTFS     23.29Gb            (XP)
/dev/sda3    ext3     14.65Gb            (Linux)
--Extended partition
/dev/sda4    swap      3.91Gb
/dev/sda5    fat32   107.14Gb            (Shared) 
---

```

I have my old hard drive (previous install of 7.04 and win 2k in it) connected up via an external HD casing using USB. 

I attempted an install, selecting the sda3 as / and formatted, bootable. Attempted to copy over old settings from sdb2 (old ubuntu). Installation failed, complaining about the Dell partition.
I then tried to do a text-mode install, installed ok but encoutered problem described above.

Retried an install via live CD, same result.

I even went to the grub prompt and attempted to manually enter the boot parameters, which are:
```

root (hd0,2)
kernel /boot/vmlinuz-2.6.20-15-generic root={UUID goes here...didn't write it down} ro quiet splash
initrd /boot/initrd.img-2.6.20-15-generic

```

I tried with the /dev/sda3 instead of the UUID.
It froze on the 'kernel ..' line. Does that mean something??

I will try to reinstall without the second hard drive being connected next, but that won't be for a while...

Thanks.

---

### Post by Co.Sinecure on 2007-06-29
Tried a reinstallation again, no luck, same thing again. Can someone please offer some guidance??

Does it have something to do with SATA drives? Order/number of partitions?? dodgy install CD???
:confused:

---

### Post by khedron on 2007-07-01
Sorry, I don't quite understand. Did the installation complete, then you copied the files from sdb2, or did you attempt to copy the files from sdb2 before you had rebooted into the new installation and set up a new user etc?

---

### Post by Co.Sinecure on 2007-07-09
> **khedron said:**
> Sorry, I don't quite understand. Did the installation complete, then you copied the files from sdb2, or did you attempt to copy the files from sdb2 before you had rebooted into the new installation and set up a new user etc?

In the graphical installation, theres a step in the install to copy files from an existing partition when you set up the options (format, etc). Actually I think you can do it with the command line install too...

---

### Post by khedron on 2007-07-09
Ok. Freezing on the kernel line implies that the installation never completed - the kernel (the core of Linux) wasn't copied over to the partition, so grub can't find it. That's the way it appears to me, anyway.

Can you remember what the error message was about the Dell partition? That seems like the best path towards correcting the problem. It shouldn't cause an error - I have a Dell partition there and my installation worked fine.

(Reinstalling Windows was a pain though - it messed up my extended partition and I had to find the partitions again with gpart and write them into a new partition table. That's another story, though. ;))

---

### Post by jbeez on 2007-07-12
Same machine with the same problem.  What is the solution?

---

### Post by khedron on 2007-07-20
> **jbeez said:**
> Same machine with the same problem.  What is the solution?

What exactly was the error message? I never found out.

---

### Post by Nolroz on 2007-07-20
I have an optiplex 320 and I cant get anything but a blank screen after the install.  I tried to replace the grub with lilo, but now I cant get my live cds to recognize my ethernet.

anybody have any ideas on how to make this work?

---

### Post by Co.Sinecure on 2007-07-25
Apologies, khedron, I haven't been able to retry since my last post.

I tried another install today, this time with Ubuntu Studio. The install seemed to run fine (as the others did), but I did have to kill apt-get when it was trying to update openoffice (my lunch hour is only so long...), and it finished off the installation. Same problem, with the blank screen and flashing cursor, indicating the kernel wasn't loading still... :(


So here's the error message the partitioner gave re: the dell partition. Comes straight after final confirmation of partition changes:
> 
File system doesn't have expected sizes for Windows to like it. Cluster size is 2k (0k expected); number of clusters is 16009 (63666 expected); size of FATs is 63 sectors (249 expected)

Warning!

                                   >Ignore<
                                      Cancel


I'm guessing that Dell's partition is meant to be that way, i.e. Windows not liking it, so that it doesn't show up in My Computer?
Still, why would that affect Ubuntu? Does the partition's wacky size mean that everything else is shifted out of line with what grub is expecting, so it's looking in the wrong place?
This is so frustrating. Seems like its a problem specific to this particular dell model...

---

### Post by Co.Sinecure on 2007-07-25
...And on that note, I found [another thread]("http://ubuntuforums.org/showthread.php?t=409345&page=2") with a possible solution (scroll down). I'll try that next.

The solution for various people seems to be installing lilo instead of grub or installing grub 2 (via the live CD)


Also, [posted on the Dell lists]("http://lists.us.dell.com/pipermail/linux-desktops/2007-January/000148.html")

---

### Post by khedron on 2007-07-26
Hope this works out for you. Tell me if it does(n't).

---

