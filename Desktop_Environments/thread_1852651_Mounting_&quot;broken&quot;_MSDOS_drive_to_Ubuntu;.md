---
title: "Mounting &quot;broken&quot; MSDOS drive to Ubuntu; &quot;Can't read superblock&quot;"
date: 2011-09-30
forum: Desktop Environments
---

### Post by fast_ian on 2011-09-30
Hi,

A buddys HD died and I convinced him to let me install Ubuntu (11.04) onto the new drive - Wonderful, all works a treat :)

I figured I may be able to get his (naturally un-backed up!) "priceless pictures" off it if I install it as the second drive - I can now see it with disk utility (as unpartitioned at dev/sdb) but when I try & mount it;

sudo mount -t msdos /dev/sdb /home/ian/foo

I get;

Can't read superblock

FWIW, Both the new & broken drives are connected via SATA, but disk utility reports them both as being on "Port 1 of PATA host adaptor"....

I googled around but nothing eases my pain - Anyone got any bright ideas? [I'd be a hero if I could get his pix off it but I'm out of experience here..... Another alternative may be "Spinrite" - any experience with it?]

TIA, cheers,
Ian

---

### Post by Shazaam on 2011-09-30
Testdisk might work...

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by matt_symes on 2011-09-30
Hi

> sudo mount -t msdos /dev/sdb /home/ian/foo

You don't mount a hard drive, you mount a partition.

If it is unpartitioned because of a corrupted drive then have a look at restoring the partition using testdisk. It's in the repositories.

Kind regards

---

### Post by kurt18947 on 2011-09-30
No experience with testdisk but if it were me, I'd try to create an image of the unreadable partition(s) before going at it with testdisk. That way if testdisk makes a total hash of it, you might be able to restore the image and try something else. Clonezilla is one popular choice for creating images, there are others.  This presumes that there are partitions that are unreadable.

---

### Post by fast_ian on 2011-10-18
Been away for a while, but back "back on the case".....

> **Shazaam said:**
> Testdisk might work...

Thanks for that. More below.

> **matt_symes said:**
> You don't mount a hard drive, you mount a partition.

Duh! Sorry 'bout that!.....

> **kurt18947 said:**
> No experience with testdisk but if it were me, I'd try to create an image of the unreadable partition(s) before going at it with testdisk.

Any idea how to go about that?...... I did attack it with TD but unfortunately didn't get anywhere; It says the first thing is the drive must be seen at the correct size - It's 80GB but disk utility is reporting is as ~6GB - BIOS seems good and there's no jumpers on the sucker so it seems there's no point in proceeding with TD.

I did however obviously push on regardless; It first reported "broken, do you want to delve deeper" (or something close to that) - I said yes and it generated a big old report with a bunch of errors then "stopped".

Any ideas? Thanks again guys - Great group here!

Cheers,
Ian

---

