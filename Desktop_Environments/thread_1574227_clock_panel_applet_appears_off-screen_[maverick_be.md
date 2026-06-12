---
title: "clock panel applet appears off-screen [maverick beta]"
date: 2010-09-14
forum: Desktop Environments
---

### Post by Nycticorax on 2010-09-14
[Maverick beta] When I click on the clock panel applet, it appears off the screen to the top (only the lower portion visible). Anyone else seeing poor positioning of this date/time/location window?

---

### Post by mike2357 on 2010-10-09
Yes.  For a discussion and work-around, see [https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/614650]("https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/614650").

If you want to use the "Place Windows" plugin (one of the work-arounds), install the CompizConfig Settings Manager.

If you want to switch to metacity (another work around), select System->Preferences->Appearance, then on the Visual Effects tab, select None.  Then, select Applications->System Tools->Configuration Editor, and navigate to Apps->Metacity->General, and check the "compositing_manager" box.  Then log out and then log back in.

---

