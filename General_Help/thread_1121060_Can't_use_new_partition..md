---
title: "Can't use new partition."
date: 2009-04-09
forum: General Help
---

### Post by ikisham on 2009-04-09
Hi, I deleted my Windows partition and formatted to ext3 but I'm not being able to use it. It shows the 'lost+found' folder but I can't create any folder nor paste anything there. (I also resized my extended partition to encompass the new one but that didn't change anything - not that I knew what that meant to do...).
The former Windows partition is the /media/disk-1. Also if anybody knows if I can free the 218.99 MB used, I will appreciate.

---

### Post by taurus on 2009-04-09
If you want to write to /media/disk-1 without becoming root, then you need to change the ownership of /media/disk-1 from root to your login name, Usuario.

```
sudo chown -R Usuario:Usuario /media/disk-1
ls -la /media
```

---

### Post by ikisham on 2009-04-09
Thank you very much!

---

### Post by lightpriest on 2009-04-09
If you'd want you could just join the two partitions to one.

You can unmount /dev/sda7 (right click on it and unmount) and then resize /dev/sda5 to contain it (gparted calls it "Move to the left" when it is performing the tasks).

Please notice if you really do so. You could not resize a mounted partition (your /) and you can't unmount it. I haven't checked what happends if you unmount it but my guess is it won't result in a running OS. :)
You could however, run from a Live CD (which contains gparted AFAIK) and perform the operations from there.

NOTICE: This MIGHT break your boot loader since the order of your partitions is changed. "MIGHT" because I'm not sure how gparted will reorder the partitions or if you still use UUIDs to mount your filesystems. After you do this /dev/sda5 will probably still be the partition so it's safe to say everything would work but you never know. So use with caution.

---

