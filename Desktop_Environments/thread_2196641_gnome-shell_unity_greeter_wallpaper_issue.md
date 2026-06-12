---
title: "gnome-shell unity greeter wallpaper issue"
date: 2013-12-30
forum: Desktop Environments
---

### Post by cybergalvez on 2013-12-30
I am running gnome-shell off a standart ubuntu 13.10 install. If I turn off "Have file Manager handle the desktop" from the gnome Tweak tool (to give the desktop a nice clean clutter free look) then when I change my desktop wallpaper the change is not reflected in lightdm. If I let Nautilus manage the desktop then it works. 

Is there any way to change the wallpaper in lightdm for a user without having Nautilus manage the desktop?

---

### Post by Frogs Hair on 2013-12-30
If have file manager handle desktop is disabled so is the ability work with files or their contents on the desktop . The right click/ context menu is also disabled. Ubuntu Tweak has a setting for separate greeter wallpaper , but don't know if it works with the gnome shell since it uses the Mutter window manager instead of Compiz.

---

### Post by cybergalvez on 2013-12-31
I looked at ubuntu tweak and didn't see where the option to change the greeter wallpaper was. And your correct if the file manager is not handling the desktop then you can not work with files on your desktop, which is the point, it keeps it nice and clutter free. The loss of the greeter wallpaper updating is a negative side effect which I was hopping there was an easy fix for

---

### Post by Frogs Hair on 2013-12-31
You can disable or enable desktop icons without disabling desktop handling from the Tweak Tool , so I don't know what is meant by clean. It is nice to be able to drag a file or photo to the desktop temporally when moving things if needed. The setting in Ubuntu Tweak is login settings.

---

### Post by cybergalvez on 2014-01-01
Actually what I had tried was unity tweak, so when I realized that I was hopeful and gave ubuntu tweak a try, not sure what I did but now nothing will boot, good think I was experimenting in a VM so nothing is really lost. I'll rebuild the VM and give it another try this time paying more attention

---

### Post by cybergalvez on 2014-01-02
So after rebuilding my VM it looks like ubuntu tweak will change the lightdm wallpaper as advertised. Still wondering if there is something that will do it automatically when my wallpaper changes since I have an extension that does it automatically.

---

