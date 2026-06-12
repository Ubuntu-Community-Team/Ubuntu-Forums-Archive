---
title: "Boot Problem (XGL?)"
date: 2007-05-07
forum: Desktop Environments
---

### Post by AdHavoc on 2007-05-07
I recently got my FGLRX driver working correctly, and so I decided to install XGL.  I followed the guide at Beryl Project, but now whenever I boot into Ubuntu, everything loads (seemingly) fine, except as soon as the load bar is finished, it goes to a black screen with the loading cursor.  I am able to move it around, so everything seems to be fine, but it just stays loading for hours on end.  Using recovery mode, I can use "startx" to go into a root session, but I want to set it back so I am able to log on the normal way using my own profile.

---

### Post by organica on 2007-05-07
> **AdHavoc said:**
> I recently got my FGLRX driver working correctly, and so I decided to install XGL.  I followed the guide at Beryl Project, but now whenever I boot into Ubuntu, everything loads (seemingly) fine, except as soon as the load bar is finished, it goes to a black screen with the loading cursor.  I am able to move it around, so everything seems to be fine, but it just stays loading for hours on end.  Using recovery mode, I can use "startx" to go into a root session, but I want to set it back so I am able to log on the normal way using my own profile.

I don't use the FGLRX driver, but I think the black screen may be due to a missing line in your xorg.conf file relating to turning on the composite extension.  Anybody want to add some insight?

---

### Post by AdHavoc on 2007-05-07
*Bump*

I have tried everything, to no avail.  I can boot into root just fine, but I really want to use my own profile.

---

### Post by organica on 2007-05-07
> **AdHavoc said:**
> *Bump*

I have tried everything, to no avail.  I can boot into root just fine, but I really want to use my own profile.

You may just have to uninstall XGL, buddy.  I can't give you anymore insight on this issue.  sorry!

---

### Post by AdHavoc on 2007-05-08
I tried uninstalling XGL and deleting all files I created in the install process.  However, it still freezes up with the loading cursor just after the kernel loads.

---

### Post by AdHavoc on 2007-05-09
*Update*

I disabled the FGLRX proprietary driver, but I still get the same boot issue.  I hope I don't have to reinstall again.

---

