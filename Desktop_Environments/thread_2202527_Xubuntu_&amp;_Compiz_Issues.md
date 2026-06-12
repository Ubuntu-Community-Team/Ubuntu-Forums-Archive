---
title: "Xubuntu &amp; Compiz Issues"
date: 2014-01-29
forum: Desktop Environments
---

### Post by Sam_Hooker on 2014-01-29
Hi all,

Just installed Xubuntu 13.10 after a hiatus from linux, and I'm having a couple issues getting fully set up.  I went to get compiz up and running, but even after installing comipiz, the restricted extras, emerald and other dependencies, I still have some wonkiness.  When I run "compiz --replace" (not stable enough to run from startup yet), my basic window enhancements & workspace settings load up, as well as the default emerald theme.  However, when i try to do a number of things (enable wobbly windows, change emerald theme, enable desktopcube/rotate desktop), compiz breaks in any number of ways.  It ranges from losing my window bars until i revert to another window manager, freezing, or just a black screen that requires a hard reboot.  

I have dconf-tools as well, changed the default theme to greybird.  

Any help would be appreciated

---

### Post by egeezer on 2014-01-30
Compiz has gone though a lot of changes in the past couple of years, and it isn't as stable as it used to be.  One comment: did you use greybird or Greybird (you do need the capital)?
And here are some notes I used to use to set things up:
  	 	 	 	   Open CompizConfig Settings Manager via Xubuntu's Settings Manager and **activate the following plugins **(without these plugins enabled, Compiz won't work properly): Composite, Gnome Compatibility, OpenGL, Window Decoration, Move Window, Resize Window, Place Windows.
 (And don't enable the Unity plugin!).

---

