---
title: "change partition name?"
date: 2009-05-04
forum: General Help
---

### Post by firsttimeuser on 2009-05-04
Hi, how can I change partition name from one to another? I am using Ubuntu server 9.04
I see the following entry under /etc/fstab, and I want to change the partition to /data. Do I just need to change the /test to /data and reboot?
Any other things I need to do? thanks!

/dev/sdb1        /test     ext3    relatime 0       2

---

### Post by Headbanger2510 on 2009-05-04
i`m not that shure, so please do more research before tring this out, but you could boot from a live ubuntu cd (or usb) and use the partition tool in the cd to rename the partition.

---

### Post by Locutus_of_Borg on 2009-05-04
```
sudo umount /dev/sdb1
sudo mkdir /data
sudo mount /dev/sdb1 /data
sudo -i
sed -e "s/test/data/ig" /etc/fstab > /etc/fstab1 && mv /etc/fstab1 /etc/fstab
```

that *should* do it, but maybe backup fstab first with: sudo cp /etc/fstab /etc/fstab_backup

just in case there are other instances of "test" inside fstab you dont want changed to read "data"


if you just want to change the label, you should be able to unmount it than use e2label, e.g.
umount /dev/sdb1
e2label /dev/sdb1 NAME

---

### Post by BslBryan on 2009-05-04
Try remounting them and changing the letters to names through fstab. 

Good luck. :)

EDIT: Locutus_of_Borg beat me to it. :P

---

### Post by Woody1987 on 2009-05-04
yes, just change it, it will work. Ive done this plenty of times. If it doesnt, just change it back, no biggie.

---

### Post by firsttimeuser on 2009-05-04
big thanks to your guys!

Will try out tomorrow morning :D

---

