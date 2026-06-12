---
title: "How does Ubuntu open workspaces?"
date: 2017-07-21
forum: Desktop Environments
---

### Post by hydra17 on 2017-07-21
Hi there. I am new to Ubuntu and Linux in general so I hope you can forgive my ignorance on the subject lol

Basically, I need to know what command Ubuntu runs when opening work spaces from the GUI. This is so that I can assign that command in CCSM to open my work spaces with hot corners. I was using this feature in Linux Mint and I quite like it, so it would be nice to recreate this in Ubuntu, now that I have switched OS.

Any help with this is much appreciated. Thank you.

---

### Post by TheFu on 2017-07-21
Which Ubuntu desktop?

I can't help with Unity, but the others follow normal X/Windows methods.  The DE sits on the Window Manager which sits on X/Windows.  Each layer handles different things. Usually, the WM handles virtual desktops, so how any specific WM does it would be documented in the manpage for that specific WM.

I haven't cared enough about virtual desktops in a long time to lookup how it is handled now. I use openbox as the WM on my systems these days. Back when I cared, fvwm was my WM and it was very clear on how to place windows into a specific virtual desktop and into a specific location on that desktop.

These days, there seems to be a tool for this ... **wmctrl** for EWMH/NetWM compatible X Window Managers.

To get a little more background, start with the wikipedia articles about "window managers" and "X/Windows" which should explain the different layering.

A big difference from how Windows does it is that the border and title area for any window you see isn't part of the program, it is part of the WM.

I'm unsure what layer CCSM fits. Sorry.

---

### Post by again? on 2017-07-21
You can use wmctrl which **TheFu** mentioned.
```
sudo apt install wmctrl
```
Compiz creates multiple virtual workspaces within your one desktop.
The dimensions of your virtual desktop depends on how many virtual workspaces you create.

For example, compiz creates workspaces to my monitor resolution of 1680x1050.
If I create 4 workspaces (2horzx2vert) each 1680x1050, my virtual desktop now has the dimension of 3360x2100.

I can use wmctrl to move to coordinates within my virtual desktop (3360x2100) which will take me to a different workspace.
In this case I am using The top left hand corner coordinates(x,y) of each workspace.

Workspace 1:
```
wmctrl -o 0,0
```

Workspace 2:
```
wmctrl -o 1680,0
```

Workspace 3:
```
wmctrl -o 0,1050
```

Workspace 4:
```
wmctrl -o 1680,1050
```

Modify for your resolution and workspace layout. Test commands in terminal.

---

### Post by deadflowr on 2017-07-22
You can set workspace overview in ccsm > Expo > bindings.
set Expo Corners/Edge to allow you to do a simple push mouse into any corner or side (top,left,right, or bottom) to "expose" all workspaces.
or you can also set Expo Button to have the same function but requiring you click a button as well; this option can help prevent you from opening the overview inadvertently.

---

