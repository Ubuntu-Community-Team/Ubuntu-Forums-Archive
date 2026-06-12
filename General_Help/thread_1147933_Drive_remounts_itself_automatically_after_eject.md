---
title: "Drive remounts itself automatically after eject"
date: 2009-05-03
forum: General Help
---

### Post by fizikz on 2009-05-03
I have an external USB hard drive that I unmount and eject using "sudo eject /dev/sdb". Since the Jaunty upgrade, after being ejected, the disk starts spinning again automatically. Why is this? The eject is successful, but the disk doesn't even stop spinning before it is 'revived' again. It does not automatically mount at that point, but I don't see why it starts up again at all.

---

### Post by fdrake on 2009-05-03
i think u should first try to unmount the to eject a media
try
```
sudo umount /media/the_folder_where_your_usb_is_mounted
sudo eject /dev/sdb
```

---

### Post by fizikz on 2009-05-03
I don't think it should be necessary since the man page for eject says that it will unmount volumes if they are mounted. But I have also tried unmounting first and it hasn't made a difference.

---

### Post by cariboo on 2009-05-03
Are you getting a notice that the drive is unmounted? If not there may be some delayed writes to the disk before it can be unmounted.

---

### Post by fizikz on 2009-05-03
I never got such notification before upgrading to Jaunty and it used to work fine. It's only since the upgrade that it won't work like it used to. Also, I imagine that unmounting first then ejecting would take care of that problem, and that didn't help.

---

### Post by fizikz on 2009-05-04
How do people typically eject an external USB drive? Unmounting works from the context (right-click) menu, but I haven't found a way to eject, or stop the disk from spinning. The command eject worked until after the upgrade. Surely I can't be the only one affected.

---

### Post by simpsonsfan74 on 2009-08-25
I have this same problem.  I've reproduced it using both USB and eSATA connected drives.  Anyone else?

---

### Post by jesuisbenjamin on 2009-08-25
it happened to before but with 1 of my 2 USB stick so i concluded it was a fault in the USB itself.

---

### Post by P4man on 2009-08-25
> **fizikz said:**
> How do people typically eject an external USB drive? Unmounting works from the context (right-click) menu, but I haven't found a way to eject, or stop the disk from spinning. The command eject worked until after the upgrade. Surely I can't be the only one affected.

I think it does the same here. It is unmounted, but it keeps spinning. Im not sure if a drive is supposed to spin down by itself, or needs to receive an instruction from the host for that..  It never really bothered me, as I tend to turn it off after unmounting anyhow, but you might consider filing a bug report if it bothers you.

---

