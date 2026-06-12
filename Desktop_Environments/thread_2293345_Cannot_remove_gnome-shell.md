---
title: "Cannot remove gnome-shell"
date: 2015-09-04
forum: Desktop Environments
---

### Post by Daniyal_Javani on 2015-09-04
I install Ubuntu 14.04 and install gnome-shell and remove it
```
sudo apt-get remove gnome-shell
```
but still inxi -S show Gnome as Desktop.
```

$ inxi -S
System:    Host: DEMON Kernel: 4.1.4-040104-generic x86_64 (64 bit) Desktop: Gnome Distro: Ubuntu 14.04 trusty
```

Could you please help me to revert to Unity?

---

### Post by deadflowr on 2015-09-04
Are you trying to remove gnome-shell as you are using it, or something?

If you want to revert to unity, you choose it from the login screen.
(There should be an icon in the right corner of the username/ password box, press it to select and change desktops)

Installing gnome-shell on Ubuntu (which has unity) does nothing to change the existence of unity.
They are two separate desktop interfaces.

---

### Post by mc4man on 2015-09-04
Ubuntu is "Desktop: Gnome"
You can run different sessions within that, to check current - 
```
echo $XDG_CURRENT_DESKTOP
```

---

### Post by Daniyal_Javani on 2015-09-05
> **mc4man said:**
> Ubuntu is "Desktop: Gnome"
You can run different sessions within that, to check current - 
```
echo $XDG_CURRENT_DESKTOP
```

Thanks, that's it!

---

