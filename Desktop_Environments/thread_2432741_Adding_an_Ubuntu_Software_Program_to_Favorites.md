---
title: "Adding an Ubuntu Software Program to Favorites"
date: 2019-12-07
forum: Desktop Environments
---

### Post by fester225 on 2019-12-07
I'm trying to add FreeCAD to Favorites.

1. When I install FreeCAD through Synaptic, installing a FreeCAD icon in Favorites is easy enough, but the program doesn't work.

2. When I install FreeCAD through Ubuntu Software, I can run FreeCAD correctly from Ubuntu Software, but I can't move a launch icon to Favorites. Although Ubuntu Software agrees FreeCAD is installed, I can't even find FreeCAD through Activities.

I have tried searching for the FreeCAD icon doing a system-wide search for the term FreeCAD. That search produced many more results than I want to go through. Even if I had found the icon, I wouldn't know where to put it.

How do I add FreeCAD to Favorites?

---

### Post by uRock on 2019-12-08
This page documents how to create the .desktop file needed in order to place some programs in the favorites menu. [https://forums.puri.sm/t/add-an-application-to-favorites-to-the-gnome-dock/3563](https://forums.puri.sm/t/add-an-application-to-favorites-to-the-gnome-dock/3563)

---

### Post by Dennis N on 2019-12-08
Caution: FreeCAD from Ubuntu Software is offered as a snap application (I searched from Ubuntu 19.04). Desktop files should be in:
```
/var/lib/snapd/desktop/applications
```
Exec= command for snap will be complex.

> I can't even find FreeCAD through Activities.
The above location should be included in the search on Activities Overview. (Note: All my installed snaps with .desktop files there are found in that search). Did you restart after installing?

To be clear, is the problem just that a program icon shows in the dock when you run the program, but does not pin as a favorite? 
If the icon is not correct, find an icon using Google Image search. In at least one snap I installed, there was no provided icon.

---

