---
title: "Drive Recognition: Basic Questions"
date: 2006-07-02
forum: Desktop Environments
---

### Post by Kurt_Alan on 2006-07-02
**[SIZE="5"][/SIZE]**

On 3/4 "Dapper Drake" LTS installs, my floppy drives fail.  Since I've never had one work correctly, I need to make a comparison:

1. When I connect a USB flash drive, its icon appears immediately on the desktop.  Should the same be true for a correctly functioning floppy drive?

2. Are drives mounted automatically in Ubuntu?  My USB drive, does not list "mount" on its menu, so I assume it's already mounted, no? (My floppy drive menu lists a mount command which fails).

Various floppy drives are various 6.06 machines are plagued with problems.  So far, my flash drive works perfectly on two machines.  So rather than try solving the floppy drive problem, I may just use the flash drive as a "work around."  On the other hand, I'm still going to install Damn Small Linux and REHL on a machine and try a couple of floppy drives.  It they work, I'd have to conclude that, at least for me, there's some problem with the Ubuntu OS . . . Time will tell.

---

### Post by dickohead on 2006-07-02
to mount a floppy disk you would need to issue the command:

sudo mount /dev/floppy
or
sudo mount /dev/fd0

Not all floppy drives or disks will be mounted automatically, but if you start the machine with the disc in the drive (one you are at the grub menu insert the disc) the machine may be more inclined to create an icon for you.

the problem with floppy drives is that they are not the most reliable pieces of equipment, you can frequently go through half a dozen drives before discovering they are all dead.

So in answer to 1 & 2:
1 - It would be nice, but i'm not sure if a floppy disc it picked up like hot-swappable USB devices are. Floppy's are old technology, flash drives are new technology, expecting them to operate in the same fashion is wishfull thinking.

2 - see above...

---

