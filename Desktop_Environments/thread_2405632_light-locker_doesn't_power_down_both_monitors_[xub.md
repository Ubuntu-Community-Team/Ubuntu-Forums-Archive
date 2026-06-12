---
title: "light-locker doesn't power down both monitors [xubuntu 18.04]"
date: 2018-11-08
forum: Desktop Environments
---

### Post by MortenGuldager on 2018-11-08
I upgraded my dual monitor **xubuntu** desktop machine from 16.04 to **18.04**.

Now **light-locker** blanks both monitors as it should, but it **only powers one of them down**.

Both xubuntu's native XFCE Power Manager and [FONT=Courier New]xset dpms force off[/FONT] are able to control power down on both monitors, just not light-locker.

**I need some guidance on how to investigate and solve this.**

Light-locker power management appears to be an old classic; most answers goes along the lines "uninstall light-locker and use xscreensaver". I can do that, but it seems backward.

---

### Post by Autodave on 2018-11-09
Hopefully someone with a better idea will jump in here, but upgrading from one release to another rarely works without issues.  I always backup everything to an external drive and do clean installs.

---

### Post by #&amp;thj^% on 2018-11-09
I have also seen problems with lightlocker/xscreensaver conflicts in the past with Lubuntu/Xubuntu.

I just prevented lightlocker from automatically starting by executing
```

sudo mv /etc/xdg/autostart/light-locker.desktop /etc/xdg/autostart/light-locker.desktop.bak
```

This is totally reversible should it cause any problems.
NOTE: there is probably a more elegant way.

---

### Post by MortenGuldager on 2018-11-10
> **1fallen said:**
> I have also seen problems with lightlocker/xscreensaver conflicts in the past with Lubuntu/Xubuntu.

Ah yes, we are not alone with our light-locker *issues*

> **1fallen said:**
> 
I just prevented lightlocker from automatically starting by executing
```
 sudo mv /etc/xdg/autostart/light-locker.desktop /etc/xdg/autostart/light-locker.desktop.bak 
```

This is totally reversible should it cause any problems.
NOTE: there is probably a more elegant way.

And I could do the same, simply dumping light-locker altogether and go with something else, say xscreensaver. But I kinda like light-lockers clean and simple system, if I just could get it working properly.

---

