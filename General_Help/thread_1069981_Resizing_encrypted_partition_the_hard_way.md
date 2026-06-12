---
title: "Resizing encrypted partition the hard way?"
date: 2009-02-14
forum: General Help
---

### Post by zongpog on 2009-02-14
Hi all,

  I have my linux partition encrypted via Twofish on an LVM for root and swap (holds everything) and I have a load of spare disc space unallocated at the end of the disc.

I know that I cannot simply grow the partition /dev/mapper/sda3_crypt so what I would like to do is this:

1) Copy off all the files in the partitions  /dev/mapper/mypc--vg-root--lv onto a USB disc drive.  Proably with,
find / |cpio -pdm /media/usbdrive/backup_root  (or use tar?)

2) Use the alternative boot CD to create the new encrypted LVM setup on dev/mapper/sda3_crypt but with the additional spare space I mentioned above.

3) Cpio (or tar) the backed up root disc onto the new partition, and then boot off it.  

During this process /boot won't be touched as its elsewhere on the disc in /dev/sda5.  It will still point to the same device because I do not intend to change these names.

Is this idea workable. I don't wish to reinstall Ubuntu again because it would result in over a fortnight to get it back to the same state.

Cheers, z.

---

### Post by hyper_ch on 2009-02-14
I wrote a little howto on something similar... maybe this gives you a few clues: [http://www.howtoforge.com/set-up-a-fully-encrypted-raid1-lvm-system-p7](http://www.howtoforge.com/set-up-a-fully-encrypted-raid1-lvm-system-p7)

---

