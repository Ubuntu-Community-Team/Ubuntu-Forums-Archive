---
title: "Help with Cedega/Halo Demo/Graphics card"
date: 2007-04-08
forum: Gaming &amp; Leisure
---

### Post by edfredcoder on 2007-04-08
Hello. I am trying to get the Halo demo working with Cedega. I installed the demo fine, and I run it from Cedega. So far, so good.

The Halo demo starts, and then asks me to run the game in safe mode because my computer's specs are low. I click ok and get a window from Halo that says...

Your computer's video driver is known to have serious issues with the game. A newer version that is compatible may be available. If you wish to update your drivers, please contract you computer manufacturer for any necessary assistance.

The only clickable button in this window is exit. Oh joy.

I can play the Halo demo under windows fine, but not under Ubuntu Feisty Fawn.

When I go to System -> Preferences -> Hardware Information, it lists my graphics card as

Vendor: Intel Corporation
Device: Mobile 915GM/GMS/910GML Express Graphics Controller

Also, when running the Cedega Video System tests (Tools -> System Tests -> Video, from Cedega), it tells me my card passed OpenGL direct rendering and failed 3D acceleration. Could this be it?

A little google'ing around tells me that the Halo demo runs fine on Linux/Cedega (although Halo doesn't).

Anyone have any ideas as to how to fix the problem? I assume it involves my video card.

---

### Post by hikaricore on 2007-04-08
Open a terminal and type:

```
glxinfo | grep rendering
```

If this returns a no, search around the forums for instructions on enabling direct rendering on an intel integrated graphics card.

If it returns a yes you may be out of luck as the intel drivers for linux are lacking compared to the drivers for windows.
Basically intel gave up on linux and stopped updating their driver.  There have been some changes made by the linux community, but nothing to come close to the full ability of the card.

Also from my knowledge, halo (any version) doesn't run particualarly well under either wine or cedega.

[http://appdb.winehq.org/appview.php?iVersionId=6978](http://appdb.winehq.org/appview.php?iVersionId=6978)
[http://appdb.winehq.org/appview.php?iVersionId=2720](http://appdb.winehq.org/appview.php?iVersionId=2720)

---

### Post by edfredcoder on 2007-04-08
glxinfo | grep rendering says yes. *sigh* So am I stuck with out hardware acceleration, and therefore the Halo demo?

---

### Post by hikaricore on 2007-04-08
No you have hardware acceleration, it just that with the intel driver it kinda sucks.  :/

---

### Post by edfredcoder on 2007-04-09
Oh well. At least I can still OpenArena and ActionCube. Halo is a Microsoft product anyway, screw it!

---

### Post by hikaricore on 2007-04-09
You may wanna chackout World of Padman: [http://ubuntuforums.org/showthread.php?t=398690](http://ubuntuforums.org/showthread.php?t=398690)

If you havn't already :)  It'll knock your socks off.

---

