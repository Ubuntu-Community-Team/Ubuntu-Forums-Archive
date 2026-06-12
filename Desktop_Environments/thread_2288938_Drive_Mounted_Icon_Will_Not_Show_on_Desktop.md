---
title: "Drive Mounted Icon Will Not Show on Desktop"
date: 2015-07-30
forum: Desktop Environments
---

### Post by coljohnhannibalsmith on 2015-07-30
Hello,

In my backup account the Drive Mounted icon will not show on desktop when the drive is mounted.
I was able to configure this in my admin account; but my mind has seemed to go blank.

Thanks, Hannibal

---

### Post by mc4man on 2015-07-30
from cli it would be - 
```
gsettings set org.gnome.nautilus.desktop volumes-visible true
```

---

### Post by coljohnhannibalsmith on 2015-07-31
> **mc4man said:**
> from cli it would be - 
```
gsettings set org.gnome.nautilus.desktop volumes-visible true
```

You know, these look like registry settings; so instead of running the command line, I followed the path
in Dconf Editor to see if I would find the setting there.  I did; so I set it there. Now I know two ways to
do this.

Thanks, Hannibal

---

