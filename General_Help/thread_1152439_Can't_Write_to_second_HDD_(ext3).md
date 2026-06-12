---
title: "Can't Write to second HDD (ext3)"
date: 2009-05-07
forum: General Help
---

### Post by roman9 on 2009-05-07
Hi there,

I'm new to Desktop Linux. I had Ubuntu 9 working perfectly for a week with two 500Gb disks.

A boot disk (ext3), and a storage disk (ntfs) which I pulled out from another computer. So today I thought I would format my secondary storage disk to ext3 as well for better performance. And I used Gparted, and the partitioning operation went smoothly.

After a reboot, in the menu I went to "Places", and clicked on the disk to mount it (as I did before with the NTFS filesystem), and that mounted the disk. However, now I can't write to this disk. I don't have permissions to write to the disk. And from what I understand, it because of the way it is mounted.

I tried for hours, and couldn't get it to mount properly with write access. I tried software such as "Mount Manager", and no luck. 

Could someone please give me advice how to mount this secondary ext3 formatted disk so I have write access?

thanks,

---

### Post by logos34 on 2009-05-07
nned to change permissions and ownership

Follow [this ]("http://www.psychocats.net/ubuntu/mountlinux")
(--> bottom)

except use UUIDs in fstab.

Check the storage drive # with:

sudo blkid

and paste it into fstab entry

---

### Post by roman9 on 2009-05-07
Hah! It's so simple when you know what you're doing.
Thank You logos34!

---

### Post by logos34 on 2009-05-07
no prob

enjoy

---

