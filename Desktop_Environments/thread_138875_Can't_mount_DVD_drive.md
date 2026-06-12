---
title: "Can't mount DVD drive"
date: 2006-03-02
forum: Desktop Environments
---

### Post by OMRebel on 2006-03-02
I'm using Breezy on a HP Pavilion n5150 laptop.  Whenever I put a DVD in my drive, I can go to Places -> Computer.  When I go to open "CD ROM/DVD ROM Drive" I get the following:

"Unable to mount the selected volume"

Under details, it gives me the following:

"Warning: device /dev/hdc is already handled by /etc/fstab, supplied label is ignored
mount: /dev/hdc already mounted or /media/cdrom0 busy
mount: according to mtab, /dev/hdc is already mounted on /media/cdrom0
Error: could not execute pmount"

Any ideas?

---

### Post by Ramses de Norre on 2006-03-02
Could you give the contents of /etc/fstab?

---

### Post by OMRebel on 2006-03-02
/etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by OMRebel on 2006-03-02
I got it working.  I typed in the following and it fixed it:

  sudo apt-get install libdvdread3
  sudo /usr/share/doc/libdvdread3/examples/install-css.sh

---

