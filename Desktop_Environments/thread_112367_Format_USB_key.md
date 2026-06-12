---
title: "Format USB key"
date: 2006-01-04
forum: Desktop Environments
---

### Post by Stambo00 on 2006-01-04
I just want a little guidance on how to format a usb key with ext3.

I would also like to know what my usb key is labelled as under /dev? I dont want to accidently format one of my hard drives!

---

### Post by steve.horsley on 2006-01-04
The command **df** should give ou an idea which drive you're currently using for Ubuntu. Probably /dev/hda.

USB derves normally show up as /dev/sda, unless you already have some scsi disks. Try the command **sudo cfdisk /dev/sda** with and without the key connected. If it only works when the key is connected, you have got it. You can use cfdisk to delete any existing partitions and to create an ext3 partition, or simply change the type of the partition that's already there. Then format it with **sudo mkfs.ext3 /dev/sda1**.Now it's ready to mount.

gparted could probably do all that graphically if you prefer.

---

### Post by kaamos on 2006-01-04
You can also (install and) use gparted .

---

### Post by Stambo00 on 2006-01-04
Thankyou, your suggestions worked perfectly :eek:

---

