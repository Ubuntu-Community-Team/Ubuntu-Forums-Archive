---
title: "Window position not retained under Unity"
date: 2012-05-26
forum: Desktop Environments
---

### Post by Nick Payne on 2012-05-26
This is on a freshly installed 12.04 amd64 installation. One of the principal applications I use is the programming editor jEdit, and I normally arrange it with the window sized to completely fill the RH side of the desktop from top to bottom. If I login with the Unity desktop and start jEdit, its window appears about the width of the title bar lower than when it was closed. Close jEdit and start it again, and the window opens yet another title bar width lower - and so on - unless the window is dragged back to the wanted position, it gets lower and lower on each startup.

However, I also installed Cinnamon from the PPA, and if I login with the Cinnamon desktop, then jEdit opens at exactly the same window position each time, with no adjustment needed. So it seems that the problem lies with Unity and not with the application.

---

### Post by mc4man on 2012-05-27
This is an issue between jedit & compiz - at least here in testing each re-open of jedit drops the window 28px from previous.

The diff between unity & any other session using compiz, like Classic, (gnome-fallback), is that unity has nothing at the bottom of a Ws to prevent the window from moving off the Ws @ the bottom

In Classic. if one was to size the jedit window to less than maxed vertically you'd see it drop till it hits the bottom panel, then it won't drop any more as the panel blocks it.

Due to another related issue that has come up in compiz-0.9.8, a 2nd un-maxed window will open 1px off the Ws, there may be a fix in unity/compiz for 12.10 where all un-maxed windows  will be prevented from opening off the Ws. (or they may fix in another manner

You could file a bug on this if desired, if so maybe on jedit & add compiz-core

---

