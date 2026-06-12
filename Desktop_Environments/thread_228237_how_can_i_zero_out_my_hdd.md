---
title: "how can i zero out my hdd"
date: 2006-08-02
forum: Desktop Environments
---

### Post by cosmoshell on 2006-08-02
what is the most easy way to zero out my hard drive.

---

### Post by RAOF on 2006-08-02
```
sudo dd if=/dev/zero of=/dev/*device_to_zero*
```

Be **very** careful.  Selecting the wrong device to zero will wipe out whatever's on there.  Selecting /dev/hda rather than /dev/hda1, for example will wipe out **everything** on the drive.

You can also select if=/dev/random, if you want your drive overwritten with random data.

---

