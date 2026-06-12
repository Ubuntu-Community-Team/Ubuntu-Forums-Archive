---
title: "Installing theme ubuntu 9.10"
date: 2010-03-13
forum: Desktop Environments
---

### Post by jklopez on 2010-03-13
i'm installing a theme on ubuntu 9.10,a windows 7 theme pack from devient art and all installed well exeped gtk theme i get an error saying installation theme failed ,can't move directory over directory...mind you i'm new to ubuntu and command line interface so if you can explaine in lay terms whats going on...thanx...

---

### Post by jklopez on 2010-03-13
i'd like to add that it's the window border that i need to install,all the rest installed fine i think it's the areo-drop.tar.gz file ,here's a link to the video i watched to install it   [http://www.youtube.com/watch?v=Lcnr5-w47NE](http://www.youtube.com/watch?v=Lcnr5-w47NE)  and heres a link to the theme pack    [http://fc08.deviantart.net/fs50/f/2009/315/e/6/windows7_lookalike_theme_pack_by_jadenxtrinityx.gz](http://fc08.deviantart.net/fs50/f/2009/315/e/6/windows7_lookalike_theme_pack_by_jadenxtrinityx.gz)    thanx again.

---

### Post by VCoolio on 2010-03-13
The aero-drop folder only contains a mouse theme if I saw correctly. The only borders I saw are emerald, so install emerald and use the emerald manager to select and install the .emerald theme. Then apply emerald as window decorator by 'emerald --replace' (this will be forgotten the next time you log in) or install fusion-icon, run it, rightclick the tray icon it provides and choose emerald in the decorator submenu (add fusion-icon to your startup applications and the borders will be remembered for future sessions).

The error btw says that a folder already exists with the name that the theme-to-install has. But since installing themes only means they are extracted in ~/.themes you can do that manually yourself in a filebrowser. Emerald themes get installed in ~/.emerald/themes.

---

### Post by jklopez on 2010-03-13
> **VCoolio said:**
> The aero-drop folder only contains a mouse theme if I saw correctly. The only borders I saw are emerald, so install emerald and use the emerald manager to select and install the .emerald theme. Then apply emerald as window decorator by 'emerald --replace' (this will be forgotten the next time you log in) or install fusion-icon, run it, rightclick the tray icon it provides and choose emerald in the decorator submenu (add fusion-icon to your startup applications and the borders will be remembered for future sessions).

The error btw says that a folder already exists with the name that the theme-to-install has. But since installing themes only means they are extracted in ~/.themes you can do that manually yourself in a filebrowser. Emerald themes get installed in ~/.emerald/themes.

u rock...:D

---

