---
title: "need help with screen res"
date: 2007-09-28
forum: Desktop Effects &amp; Customization
---

### Post by valpobro on 2007-09-28
when i am running the restricted divers for my video card it only lets me use one screen res and it is not the one i want. if i disable the restricted driver i can pick what i want but the graphics are slow. how can i fix this?

i'm running ubuntu studio and have a gforce 7300gs pcie, nvidia chipset

thank you
dan

---

### Post by Mavtech on 2007-09-28
Don't use the Ubuntu settings to control the resolution.  Use the Nvidia settings in Applications --> System Tools --> Nvidia Settings.  You are then suppose to have it write to the xorg so it holds the settings for every time you log in.  But, mine was giving me an error probably due to permissions.  So, if you have this issue, use "sudo gedit /etc/X11/xorg.conf" to bring up the editor.  When you click on "Save to X configuration" after making the res changes, there will be a preview button for the xorg.  Copy all of that into your current xorg, save, exit, then restart X.  **Don't forget to back up xorg.conf before trying this.**

---

### Post by polygone on 2007-09-28
edit: beat me to it.  :P

---

