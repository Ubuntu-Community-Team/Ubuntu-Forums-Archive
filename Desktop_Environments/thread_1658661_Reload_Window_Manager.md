---
title: "Reload Window Manager"
date: 2011-01-02
forum: Desktop Environments
---

### Post by dsmo223 on 2011-01-02
I have installed Compiz on my laptop and it came with Emerald, and it seamed to work well for a while, but now it seams that I have to reload my window manager very frequently because my close, minimise, and maximise buttons will all disappear. Can anyone help me fix my problem? I am running Ubuntu 10.10. If my only option is to remove compiz, I am fine with doing that, but if so, can somebody give me step by step directions in removing it and getting back to the default settings, I am new to Linux. 


Thank you for any and all help and understanding.

---

### Post by stinkeye on 2011-01-03
No need to uninstall compiz.

You can try using the gtk-window-decorator instead of emerald with
(Use alt + F2 to run)
```
gtk-window-decorator --replace
```

or
 
To load the default Metacity window manager.
Open System > preferences > Appearance > Visual Effects 
and select **None**


Install **fusion-icon ** to easily change between window decorators and window managers.
```
sudo apt-get install fusion-icon
```
You will find the menu entry in System Tools.
fusion-icon sits in the tray ....right click for options.

---

### Post by dsmo223 on 2011-01-03
> **stinkeye said:**
> No need to uninstall compiz.

You can try using the gtk-window-decorator instead of emerald with
(Use alt + F2 to run)
```
gtk-window-decorator --replace
```

or
 
To load the default Metacity window manager.
Open System > preferences > Appearance > Visual Effects 
and select **None**


Install **fusion-icon ** to easily change between window decorators and window managers.
```
sudo apt-get install fusion-icon
```
You will find the menu entry in System Tools.
fusion-icon sits in the tray ....right click for options.
Thank you for the advise, I will try it and see what happens.

---

