---
title: "LXDE use compiz  can't add desktop pager"
date: 2011-02-15
forum: Desktop Environments
---

### Post by indosupremacy on 2011-02-15
hi , i am  using 10.04 , and i have installed lxde successfully and i try to use compiz . Yes, it can work , but the only problem with it is i can't add desktop while compiz being used as window manager . 
when compiz is activated , the desktop is always one , cant change to 2,3 or 4.
This problem also occure at this [site ]("http://forum.lxde.org/viewtopic.php?t=1439&f=8") (lxde forum) 
anybodu have the same problem?
has anyone has solved it?
thank you

---

### Post by 3Miro on 2011-02-15
Compiz works different then Openbox (the default WM of LXDE). Compiz uses one continuous desktop that is divided into several parts. Gnome-panel has a pager plugin that is hacked to work with Compiz, but even that loses some functionality.

Install Compiz-Config-Settings-Manager (CCSM) and look at the different settings for Compiz. You can adjust different workspaces as well as mouse and keyboard shortcuts to switch between them. The only issue is that the Openbox pager will probably not show correct information.

---

### Post by indosupremacy on 2011-02-15
> **3Miro said:**
> Compiz works different then Openbox (the default WM of LXDE). Compiz uses one continuous desktop that is divided into several parts. Gnome-panel has a pager plugin that is hacked to work with Compiz, but even that loses some functionality.

Install Compiz-Config-Settings-Manager (CCSM) and look at the different settings for Compiz. You can adjust different workspaces as well as mouse and keyboard shortcuts to switch between them. The only issue is that the Openbox pager will probably not show correct information.

i already have installed it , and have try to add desktop from ccsm or lxde setting manager ,but the problem still exist , anybody know the answer ?

---

### Post by JOHNNYG713 on 2011-02-16
This is a known "bug" in LXDE Panel, and they are working on it, you can install Cairo Dock or AWN Dock, They have Desktop switchers, Or you can change Desktops by rotating the Cube !

---

### Post by Bazon on 2011-10-30
or:
in compiz config settings manager, you can set in general options the size of virtual desktops to 1 (horizontal and vertical) and set the number of desktops (last row) to e.g. 6.
then the desktop pager panel applet works in lxde/lubuntu. :-)

(on the other hand, things like cube etc. don't work..)

---

### Post by fordry on 2011-11-01
I set it to horizontal size of 4, vertical 1, and number of desktops 4 and the cube works. Only issue is that the panel switcher doesn't update, still trying to figure that out, though I really only wanted compiz mainly for the window snap and window preview features. I am using lubuntu 11.10.

---

