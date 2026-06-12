---
title: "Fluxbox SD Card Mount ?"
date: 2010-01-19
forum: Desktop Environments
---

### Post by Rodney9 on 2010-01-19
Hello,

How do I mount my sd card in Fluxbox, I insert it into my Dell monitor's in-built card reader ?

Rodney

---

### Post by Rodney9 on 2010-01-19
ivman

---

### Post by Barriehie on 2010-01-21
Although solved there is a much 'lighter' way.  I plugged mine in and then ran nautilus --no-desktop and saw what the device was, /dev/sdc1 and added an automount entry to fstab.  I leave mine in for a backup of a backup so it's always inserted.

[color="green"]/etc/fstab[/color]
```

# USB Stick - 4GB
/dev/sdc1   /media/disk auto auto,user,rw,sync  0       0

```

---

