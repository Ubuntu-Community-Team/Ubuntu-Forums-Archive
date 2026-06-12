---
title: "ubuntu 8.04 install issue"
date: 2008-11-27
forum: Desktop Environments
---

### Post by Boxerriely on 2008-11-27
i can boot into recovery mode. but it wont boot up normally after install. i think it may have to do with a display issue. but where can i look to see exactly where it fails.

---

### Post by taurus on 2008-11-27
See if it works if you reconfigure your X server again.  From the recovery mode, run

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```

---

### Post by Boxerriely on 2008-11-28
i ran that command and nothing changed. it actually looks like it crashes on hardware abstraction layer hald. any more ideas.

---

