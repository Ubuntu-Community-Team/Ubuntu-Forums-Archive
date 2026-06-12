---
title: "Ubuntu 10.10 - Mac style buttons..."
date: 2010-11-07
forum: Desktop Environments
---

### Post by blackmail on 2010-11-07
Hi, I decided to move away from my 9.10 to the all new shiny 1010 ubuntu. Now my great problem is with the mac style left aligned buttons... I frankly HATE them, how could i have the old right-side buttons? Mainly I am talking about the Minimize, maximize, and close buttons...
Please help a noob with Ubuntu 10.10.

---

### Post by cipherboy_loc on 2010-11-07
To change them back, open up GCONF-Editor (alt+f4 and in the box that pops up enter gconf-editor). Click on Apps, Scroll down to and click on metacity, click on general. Right click on button_layout and select edit key. Type in "menu:minimize,maximize,close" without the quotes into the box where it says Value. Click Ok and they should change.


Cipherboy

---

### Post by blackmail on 2010-11-08
Thnx, that helped :D

---

### Post by DirtyPC on 2010-11-08
Surely you can just download a theme that will move them? I have a unity theme and my buttons are on the right on 10.10

---

