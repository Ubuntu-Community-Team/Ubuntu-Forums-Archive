---
title: "screen tearing caused by cairo-dock"
date: 2011-12-07
forum: Desktop Environments
---

### Post by w1d3 on 2011-12-07
i have cairo-dock load at startup i noticed that there was some screen tearing and looked into it and i found out that if i stop cairo-dock the screen tearing stops but then my desktop starts flickering im with 10.04 gnome+compiz+emerald

[COLOR=Red]edit:[COLOR=Black] i forgot to tell you the video card im using its nvidia[/COLOR][/COLOR] GT 240m and the laptop is Lenovo Y550
[COLOR=Red]

edit: [/COLOR]i think the problem is with the driver settings i tried all kinds of  settings for xorg.conf that i found in the nvidia wiki but they didnt  work so if anyone knows something im missing PLEASE HELP its really annoying even when im watching videos in full screen mode the video tears up..

---

### Post by thaelim on 2011-12-08
Are you using the nVidia binary drivers? Have you tried adjusting the OpenGL Vsync setting in the nVidia control panel?

---

### Post by w1d3 on 2011-12-10
> **thaelim said:**
> Are you using the nVidia binary drivers? Have you tried adjusting the OpenGL Vsync setting in the nVidia control panel?

yeah im with the drivers and i have tried everything setting up xorg.conf and etc.

---

### Post by w1d3 on 2011-12-14
anyone??

---

### Post by thaelim on 2011-12-16
[LIST=1]
[*]Ensure BOTH  OpenGL and XVideo vsync is turned on in nVidia settings
[*]Ensure Sync to Vblank is enabled under OpenGL in compizconfig-settings-manager
[*]Reboot (this is needed to apply settings for the nVidia card)
[/LIST]

---

