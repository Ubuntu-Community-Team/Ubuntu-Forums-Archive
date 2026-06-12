---
title: "Dell pre-installed laptop - do I need these partitions?"
date: 2009-02-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kiwi8mail on 2009-02-01
I am in possession of a Dell Inspiron 1525 with Ubuntu pre-installed. The hard drive already contains a number of existing partitions - I've created a list below my posting.

Do I need to keep the fat32 partition? It has a [misleading?] label of "OS" and mounts as a separate drive on startup. It seems to be some sort of recovery partition, containng material in a variety of folders (named: casper, debs, dists, docs, grub, isolinux, misc, pool, preseed, and scripts). I've made recovery disk anyway (a link/utility on the desktop encourages me to do this) which just copies the files in this partition to a DVD

Also what about the fat16 partition - what is that for?

Thanks for any assistance on this - the documentation from Dell on Ubuntu is pretty-much non-existent, but I do have some prior experience with Ubuntu.

EXISTING PARTITIONS:
The 250GB drive came from the factory divided as follows:
/dev/sda1 A fat16 partition of 109MB, only 9MB of which is used
/dev/sda2 A fat32 partition of 3GB, 1.87GB of which is used.
/dev/sda2 An ext3 partition of 228GB, of which about 10GB is used. This is of course the boot partition
/dev/sda4 A 1.92GB extended partition
/dev/sda6 A 1.92GB linux-swap partition

---

### Post by hyperdude111 on 2009-02-01
All ubuntu needs to run is the ex3 partition. However i recomend you keep a 1-3 gb swap partition as it is used as extra RAM whn the physical ram is empty.

---

### Post by ugm6hr on 2009-02-01
My theory:

sda1 = Dell Diagnostics (accessed from BIOS)
sda2 = Dell Recovery (to reinstall Ubuntu)
sda3 = Ubuntu
sda4/6 = swap partition

In theory, you need only sda 3/4/6.

However, removing partitions may rename the disks in Grub etc, so I would leave them alone.

If you really need the extra 3GB on a 250GB HD, then ask for more detailed advice on how to do it.

Be aware that future support from Dell may be affected by you deleting those partitions though.

---

### Post by gbrainin on 2009-02-01
ugm6hr is indeed correct regarding the nature of the partitions.  This is detailed on the Dell Linux Wiki [here]("http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Default_Partitions").

In my experience, the diagnostics partition is useful when talking to Dell tech support about problem hardware.  Plus, it's tiny.

The reinstall partition can be useful.  If you mess up your system, it's a foolproof way to get it back.  However, be warned that it will _repartition and reformat_ your drive to the exact state it was in when you bought it.  You will lose all changes.

The main Linux boot partition is, of course, where the Linux filesystem is.  Personally, I prefer to have a separate partition for /home, which makes upgrading a bit easier (you can reformat your / partition without affecting your personal directory).  I followed the instructions [here]("http://www.psychocats.net/ubuntu/separatehome") to do this, but obviously it's optional.

Finally, Linux likes having a swap partition (which must be a separate partition, as it is a different format), and again, it's small.

So, strictly speaking the only partition you _need_ to run Ubuntu is the ext3 partition, but I found the other partitions useful enough (and small enough) that I've kept them around.  YMMV.

---

