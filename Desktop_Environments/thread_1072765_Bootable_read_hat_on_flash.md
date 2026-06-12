---
title: "Bootable read hat on flash"
date: 2009-02-17
forum: Desktop Environments
---

### Post by jmecosta on 2009-02-17
Hi,

I guess this might not be an adequate place to put this thread, but i hope someone has some suggestion to me.

This is my problem:

Need to create a bootable device to deploy in a embedded  device (flash disk). I've check that this is possible to do with syslinux (extlinux), but the idea is to use a current file system that i've defined in a directory (/bin /usr /root /home /boot /etc) (red hat system) and deploy it and install LILO a configure it to correctly boot it.

So the idea is to have a ext3 partition, copy all the files to the flash disk partition and write the MBR to correctly boot the system using LILO.

If anyone has suggestions, i would really appreciate it.

Regards

---

