---
title: "U 15:10 bg problem"
date: 2016-03-27
forum: Desktop Environments
---

### Post by Frank_Rubi on 2016-03-27
For some reason or another, whenever I open the files icon it changes my background. I'm running 15:10 with Cinnamon, I just couldn't get used to unity.

---

### Post by QIII on 2016-03-27
*Moved to **Desktop Environments***.

Let's see if you don't get some better DE-specific help here.

---

### Post by ajgreeny on 2016-03-27
I presume you mean nautilus file-manager when you talk of the Files icon; correct?

If so, you need too edit the nautilus.desktop file (which is what that icon really is) and change the line ```
Exec=nautilus
```or it may also be ```
Exec=nautilus --new-window %U
``` to ```
Exec=nautilus --no-desktop
```
Your current problem stems from the way nautilus will always manage the desktop of any DE if you do not use the **--no-desktop** option, thus taking over from whatever file-manager normally manages the desktop in cinnamon

---

### Post by Frogs Hair on 2016-03-29
Does Cinnamon include Nemo file manager ? If so use Nemo rather than Files/Nautilus.

---

### Post by montag dp on 2016-03-29
Or use Linux Mint if you want the best Cinnamon experience. It will be harder with Ubuntu since Cinnamon has several components (like Nemo) that don't play nice with the Gnome based environment of Ubuntu.

---

