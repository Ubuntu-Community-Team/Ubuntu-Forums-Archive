---
title: "How to remove another menu Bar (alt+R-click does not work)"
date: 2012-03-04
forum: Desktop Environments
---

### Post by ggtutu on 2012-03-04
As you can see, I am using the gnome classic with Cairo dock.
I removed the default bottom bar, and removed most of the icons on the default top bar then shortened&dragged it to the RIGHT. 

I have being playing with some settings including PAE kernel (uninstalled already) and etc, then after a reboot, ANOTHER top menu bar showed up. I failed to remove it. the "alt+R-click" does not work, no right-click menu showed up.

Any ideas?

---

### Post by Krytarik on 2012-03-04
This will disable Global Menu - incl. that of Nautilus, which you are currently seeing - in any non-Unity sessions:
```
echo '[ ${DESKTOP_SESSION#ubuntu} = $DESKTOP_SESSION ] && unset UBUNTU_MENUPROXY' | sudo tee /etc/X11/Xsession.d/81ubuntu-menu-proxy
```You need to relogin for the change to take effect. If you want to revert that later, just remove the created file.

Regards.

---

### Post by ggtutu on 2012-03-05
Thanks a lot, it worked.

Just out of curiosity, how do you get to know tricks like this?

---

### Post by Krytarik on 2012-03-05
> **ggtutu said:**
> Just out of curiosity, how do you get to know tricks like this?
Lurking around the Ubuntu Forums day and night. :P (Ok, mostly at night. ;-) )

---

### Post by ggtutu on 2012-03-05
> **Krytarik said:**
> Lurking around the Ubuntu Forums day and night. :P (Ok, mostly at night. ;-) )

I thought you were one of the gnome devs out there.:D There is absolutely no way to figure it out all by myself.

Thanks again.

---

