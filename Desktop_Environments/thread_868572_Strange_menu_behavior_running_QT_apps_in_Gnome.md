---
title: "Strange menu behavior running QT apps in Gnome"
date: 2008-07-24
forum: Desktop Environments
---

### Post by schauerlich on 2008-07-24
I have a few QT apps that I run under gnome (amaroK, Dolphin and Opera) and whenever I click on one of the menus in the menu bar, the menu opens up twice and there's a border around it. Is there a fix for this?

Picture of the problem attached.

---

### Post by jensbw on 2009-03-09
> **EDavidBurg said:**
> I have a few QT apps that I run under gnome (amaroK, Dolphin and Opera) and whenever I click on one of the menus in the menu bar, the menu opens up twice and there's a border around it. Is there a fix for this?

Picture of the problem attached.

KDE 3 draws it's own shadows. What you see is basically the KDE shadow getting a double shadow due to the window manager creating a secondary shadow underneath. I don't have KDE 3 installed at the moment but it should be possible to disable this KDE desktop effect somewhere in the KDE theme control panel.

---

### Post by hihihi on 2009-03-17
i have exactly the same problem under KDE4.2.1... this is a bug, i think, did u report this bug? anybody has an idea how to get rid of this problem?

---

