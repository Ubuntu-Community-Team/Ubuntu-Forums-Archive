---
title: "Compiz Fusion Help"
date: 2008-03-18
forum: Desktop Effects &amp; Customization
---

### Post by LinuxNewb092 on 2008-03-18
Hey guys I was wondering how to make it so I can see a cube and rotate it around. Heres a link for an example, [http://www.youtube.com/watch?v=bvnQE1EAEZY](http://www.youtube.com/watch?v=bvnQE1EAEZY).
What I want to do starts on 0:14 and stops on 0:20 of the video. I was also wondering what dock he had if anyone could tell me please.

---

### Post by mk1w86 on 2008-03-18
Install the compizconfig-settings-manager package:

Type 

sudo apt-get install compizconfig-settings-manager

into the terminal to install. (Applications >> Accessories >> Terminal)

Once the compiz setting manager is installed goto:

System >> Preferences >> Advanced Desktop Effects Settings 

From here you can configure all the compiz fusion desktop effects.  To enable the cube tick the 'Desktop Cube' box and to enable rotation of the cube tick the 'Rotate Cube' box.  By default you press Ctrl+Alt and Left click and move the mouse to rotate the cube.

To configure the cube further you click the text e.g. 'Desktop Cube' to the right of the tick box in the compiz settings manager.  If the cube doesn't work at first you may have to fiddle with some of these settings - sometimes the number of workspaces can cause problems.

The dock might be the cario dock although I am unsure.

---

### Post by Therion on 2008-03-18
[How to Setup Compiz Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion).

---

### Post by mk1w86 on 2008-03-18
Regarding my last post I assume you have compiz working on your computer.

If not make sure you have installed the restricted drivers for your graphics card (System >> Administration >> Restricted Drivers Manager).

To enable the preset Ubuntu set of effects goto:

System >> Preferences >> Appearance >> Visual Effects tab and choose Normal or Extra.

If you have installed the compiz settings manager from my last post then you will also have a Custom option which will get selected when you enable the cube because the cube is not enabled in the default set of effects.

---

