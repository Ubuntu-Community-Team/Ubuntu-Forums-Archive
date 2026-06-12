---
title: "Remove window minimize animation ?"
date: 2006-06-08
forum: Desktop Environments
---

### Post by Vilius on 2006-06-08
How to do that ?

---

### Post by aysiu on 2006-06-08
Alt-F2 ```
gconf-editor
``` Apps > Metacity > General > Reduced Resources

---

### Post by Video Toaster on 2006-06-08
[QUOTE=aysiu]Alt-F2 ```
gconf-editor
``` Apps > Metacity > General > Reduced Resources[/QUOTE]
Be aware, though, that this will cause Metacity to use wireframe outlines when resizing/moving windows.

---

### Post by aysiu on 2006-06-08
[QUOTE=Video Toaster]Be aware, though, that this will cause Metacity to use wireframe outlines when resizing/moving windows.[/QUOTE]
Unless you enable Assistive Technology Support in System > Preferences.

---

### Post by mcduck on 2006-06-09
There's also apps/panel/global/enable_animations (or something like that, I'm not at my Ubuntu box atm) that disables animations when minimizing/maximizing windows, but doesn't make windows wireframes when moving.

---

### Post by Vilius on 2006-06-09
Thanks guys,
the pair of options 'Apps > Metacity > General > Reduced Resources' + 'enable Assistive Technology Support' works great.

however 'apps/panel/global/enable_animations' not worked for me.

---

### Post by mcduck on 2006-06-10
[QUOTE=Vilius]Thanks guys,
the pair of options 'Apps > Metacity > General > Reduced Resources' + 'enable Assistive Technology Support' works great.

however 'apps/panel/global/enable_animations' not worked for me.[/QUOTE]
You have to *disable* that option to get rid of those animations..

---

### Post by Lunar_Lamp on 2006-06-16
Is there a way to get rid of the ugly black line animation, but replace it with a more 'normal' animation?

---

