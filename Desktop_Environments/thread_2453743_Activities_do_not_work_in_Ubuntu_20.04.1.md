---
title: "Activities do not work in Ubuntu 20.04.1"
date: 2020-11-16
forum: Desktop Environments
---

### Post by Malfet on 2020-11-16
Hi all,

I recently upgraded to Ubuntu 20.04.1. Unfortunatly, Activities do not show overview of all open windows in the worspace. I just get a search bar on top of the screen while the rest of the screen is occupied by the window of the active app. I try to asked this question on Ask ubuntu with zero replies. Google and Forums search do not give any hints as well... Please, help! I probably need to downgrade back to the old version, because this is a real pain.

Thanks!

---

### Post by Frogs Hair on 2020-11-19
There is no downgrade path to previous versions. Was this an upgrade from 20.04 or 19.10?

---

### Post by Malfet on 2020-11-20
From the preivous LTS 18.04. I was really waiting for long time before the upgrade to make sure that they will fix such kind of EXTRA BIG OBVIOUS bugs :(:(:(

---

### Post by Frogs Hair on 2020-11-20
As suggested on GITlab,  check for outdated gnome-shell extensions and try disabling installed extensions one by one to see if there is any change. I don't know if looking glass is still in use, but it is/was a trouble shooter for the gnome-shell. Type Alt + F2 and enter the following. ```
lg 
```

---

### Post by Malfet on 2020-11-22
Actually I observed that behaviour even on the completely fresh installation and it seems to be caused by Workspaces to Dock extension. Of course I can disable it... but this is most useful extension among all gnome extension, in my opinion! Anyway. I think, I just have to wait until they find a solution and fix it.

---

