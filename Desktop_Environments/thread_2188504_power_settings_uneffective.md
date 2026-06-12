---
title: "power settings uneffective"
date: 2013-11-17
forum: Desktop Environments
---

### Post by d-geoffm on 2013-11-17
I set "when laptop lid is closed - do nothing" but when I close the lid the laptop goes on standby. I don't see what the point is to fake giving the user a choice if the DE does whatever it wants...

---

### Post by tgalati4 on 2013-11-17
Perhaps there is a setting in Power Management in BIOS?  BIOS will often override settings in userland.

---

### Post by Toz on 2013-11-17
> **d-geoffm said:**
> I set "when laptop lid is closed - do nothing" but when I close the lid the laptop goes on standby. I don't see what the point is to fake giving the user a choice if the DE does whatever it wants...
If you are using version 13.10, then you may need to edit /etc/systemd/logind.conf and replace:
```
#HandleLidSwitch=suspend
```
...with:
```
HandleLidSwitch=ignore
```

Reference: [https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1222021]("https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1222021").

---

