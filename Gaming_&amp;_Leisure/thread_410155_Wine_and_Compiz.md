---
title: "Wine and Compiz"
date: 2007-04-15
forum: Gaming &amp; Leisure
---

### Post by Cleves on 2007-04-15
Hi all,

I've installed FM2007 using Wine and everything was okay. Then I installed Compiz and since then FM2007 won't work. It would display the message "Unable to load fullscreen mode" and in terminal it would write:
```

err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (NoRes)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (NoRes)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (NoRes)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (NoRes)

```

Any ideas?

Thanks in advance.

---

### Post by The Noble on 2007-04-15
It looks like xorg.conf got corrupted or something. this may screw up compix, but running 
```

sudo dpkg-reconfigure xserver-xorg

```
may solve the problem.

---

### Post by Cleves on 2007-04-15
Nope, didn't work.

Any other ideas?

---

