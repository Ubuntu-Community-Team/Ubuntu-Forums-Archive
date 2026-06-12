---
title: "Windows XP on side of Compiz Cube using VMware"
date: 2007-11-18
forum: Desktop Effects &amp; Customization
---

### Post by johndavid400 on 2007-11-18
has anyone been able to put windows XP on one side of the Compiz fusion cube face using VMware server and Gutsy?

I have seen that people got it to work using beryl...what about compiz?

I cant seem to figure out how once on the windows xp fullscreen, to switch to another cube face, since all input is captured for XP and to release the keyboard (alt+ctrl) bumps you out of fullscreen!

Any ideas?

---

### Post by mrmiserable on 2007-11-18
change key config in ccsm for rotate cube

---

### Post by Scunizi on 2007-11-18
I changed the screen resolution of windows to be smaller than my screen.  Place the mouse outside of the VM box and rotate as normal.

---

### Post by johndavid400 on 2007-11-19
change key config to what? all keyboard input is captured... unless i'm missing something.

---

### Post by mrmiserable on 2007-11-19
in compizconfig settings manager/rotate cube/actions
double click initiate
and change this to whatever you want it to be so as not to conflict with vmware key settings

---

### Post by Scunizi on 2007-11-19
On playing with it I've found another way that works for me.  When full screen in XP and needing to rotate the cube to another desktop, hit Ctrl+Alt to release the mouse from the VM and then rotate as normal with key combinations or by mouse drag (after hitting crtl+alt again and holding.)  I'm glad I discovered this 'cause I was running the vm in 1024 x 768 on my monitor which supports 1280x1024.  My vm is now set for 1152x864 which works well.

---

### Post by xardy on 2007-11-19
I use virtualbox with winxp fullscreen on one workspace and switch to others with the expo plugin, I just set it so that when i move my mouse to the bottom right corner of my screen with my mouse expo jumps in.

I gues you could do the same with the cube, let it iniate by moving your mouse to a screen edge.

---

### Post by MNICY on 2007-11-20
Ive done it with virtualbox.
Seamless mode, on one side of the cube.

---

### Post by johndavid400 on 2007-11-25
ok, I installed Virtual Box and XP and enabled the screen-edge-flip to rotate the cube and all is good. I am able to do what I wanted to. 

I re-set the number of desktops from 4 to 2, so instead of having a 4 sided cube, I now have a 2 sided flat desktop. On one side is Ubuntu, on the other Windows XP. Instead of having them share a network address, I opted to allow XP it's own IP address. Now I can share files between the two over the network.

Awesome. And thanks for your help.

---

