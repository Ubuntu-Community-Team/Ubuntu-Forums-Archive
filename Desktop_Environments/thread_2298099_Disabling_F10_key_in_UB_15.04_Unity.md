---
title: "Disabling F10 key in UB 15.04 Unity"
date: 2015-10-09
forum: Desktop Environments
---

### Post by Edward_Diener on 2015-10-09
In my editor the F10 key is used to save a file. Somewhere in Unity my use of the F10 is being overridden so my editor never sees it. How can I turn off Unity's use of the F10 key ?

---

### Post by alex_32 on 2015-10-09
Hi,

You can view the shortcuts assigned to your system in **System Setting -> Keyboard -> Shortcuts. **Also some are available in the Unity Tweak Tool.

---

### Post by Edward_Diener on 2015-10-09
The F10 key appears in neither place.

---

### Post by mc4man on 2015-10-10
F10 does nothing here but still is in a dconf/gsetting for menubar-accel
```
gsettings get org.gnome.desktop.interface menubar-accel
```
Try unsetting it - 
```
gsettings set org.gnome.desktop.interface menubar-accel ""
```
A log out/in may be required to see.

If still an issue then mention the "editor" name

---

### Post by Edward_Diener on 2015-10-11
> **mc4man said:**
> F10 does nothing here but still is in a dconf/gsetting for menubar-accel
```
gsettings get org.gnome.desktop.interface menubar-accel
```
Try unsetting it - 
```
gsettings set org.gnome.desktop.interface menubar-accel ""
```
A log out/in may be required to see.

If still an issue then mention the "editor" name

Excellent ! That worked and now I can use the F10 key in my editor again. I hate it when software hides such stuff where end-users can not even normally find it.

---

