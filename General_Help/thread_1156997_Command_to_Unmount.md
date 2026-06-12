---
title: "Command to Unmount"
date: 2009-05-12
forum: General Help
---

### Post by CrusaderAD on 2009-05-12
What's the command to unmount a drive in your fstab file?

---

### Post by unutbu on 2009-05-12
You can unmount by giving the device name:
```

sudo umount /dev/sda1
```
or the mount point:
```


sudo umount /mnt/Windows
```

---

### Post by CrusaderAD on 2009-05-12
Perfect thanks! I was typing "unmount", not "umount".

---

