---
title: "Ubuntu Customize"
date: 2018-07-26
forum: Desktop Environments
---

### Post by open4epl on 2018-07-26
Is there any way to make the App Launcher Icon into any image I want? Same w/ the Favorites Bar.

---

### Post by monkeybrain20122 on 2018-07-26
> **open4epl said:**
> Is there any way to make the App Launcher Icon into any image I want? Same w/ the Favorites Bar.

Yes, just edit the .desktop file and change the Icon= line to point to whatever picture you want. The .desktop files are usually in /usr/share/applications if you installed the software from the repository. However, if you have an update of the software the  .desktop would be overwritten, so instead of doing it again, you can copy the .desktop file to ~/.local/share/applications and then edit it. This one would take precedent over the one in /usr/share/applications and won't be affected by updates.

---

### Post by coffeecat on 2018-07-27
Support, not chat.

*Thread moved to **Desktop Environments**.*

---

### Post by open4epl on 2018-07-27
What do I change in that folder to change the App Launcher Icon & Favorites Bar?

---

### Post by open4epl on 2018-07-28
Bump

---

### Post by Frogs Hair on 2018-07-28
"view-app-grid-symbolic.svg" _was_ the the name of the icon on 17.10, but I don't find it on 18.04 as described by the outdated [link]("https://www.omgubuntu.co.uk/2017/04/change-dash-dock-app-launcher-icon"). It may not be located in an icon set at all but, somewhere else in the file system.


I did locate the icon in one of my icon sets as described in the link.

---

