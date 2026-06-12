---
title: "How to enable kde compatibility in Compiz for Dockbarx Previews?"
date: 2010-07-03
forum: Desktop Environments
---

### Post by finny388 on 2010-07-03
> NOTE! To use previews you need to activate KDE Compability in compiz settings manager and under KDE Compability check "Support Plasma Thumbnails". (Alternatively you can use kwin as window manager instead of compiz. That will give you previews for minimized windows as well.)

How is this done? I have CompizConfig Settings Manager and I can't find kde anywhere.

I am running Ubuntu 10.04 (gnome)

---

### Post by kmsalex on 2010-07-03
you might want to try 
```
apt-get install compiz-fusion-plugins-extra 
```
that might get the missing option, sorry can't check first had don't have access to an ubuntu machine right now.

---

### Post by M7S on 2010-07-03
Unless something is wrong (like if you dont run compiz fusion, for example), dockbarX asks you if it should turn it on automatically when you change the option in DockbarX preference dialog.

---

### Post by finny388 on 2010-07-03
It does ask me if I want it enabled, I answer yes, but nothing happens.

Do I have to install compiz fusion?

---

### Post by M7S on 2010-07-03
Wierd, that should be it. Compiz fusion should be installed out of the box.

---

### Post by finny388 on 2010-07-03
When I installed I had these choices in Synaptic:
1 OpenGL window and compositing manager (compiz)
2 Compiz (OpenGL window and compositing manager - GNOME window decorator)
3 Compiz Fusion Icon (Start and manage Compiz Fusion)

I installed #2
After that I also installed CCSM.

Where I am I supposed to find this KDE compat. option??

Do I need to install compiz-fusion-plugins-extra as kmsalex suggests?

I am BRAND NEW to compiz. But CCSM looked very straight fwd.

---

### Post by M7S on 2010-07-03
KDE compability is in ccsm, the general section, I think (I don't have compiz on my netbook so I can't check).

---

### Post by Yuri sss on 2010-07-03
Install the packages "compiz-kde" and "compizconfig-backend-kconfig" for Kde compatibility.

---

### Post by finny388 on 2010-07-04
> Install the packages "compiz-kde" and "compizconfig-backend-kconfig" for Kde compatibility. 

done.

still nothing. see attachment for screen shots.

I tried changing "backend" (Screenshot2) to KDE but it didn't change anything.

:(

---

### Post by finny388 on 2010-07-04
I've attached a shot of Synaptic installed software filtered by compiz.

---

### Post by M7S on 2010-07-05
You could try with compiz-fusion-plugins-main, but all needed stuff was already installed right out of the box for me, so I don't understand why you needed to install compiz at all. Did you install Ubuntu in any unusual way?

---

### Post by finny388 on 2010-07-05
I installed the Netbook edition and switched to log in with Gnome desktop soon after.

Perhaps that is why compiz was not installed.

I installed compiz-fusion-plugins-main and now I finally see kde compatibility in CCSM and previews are working.

Maybe Dockbarx should at least show an error when you click yes to enable kde comp. and it fails.

Thanks M7S!

---

