---
title: "[SOLVED] Where is icon located?"
date: 2008-11-11
forum: Desktop Environments
---

### Post by jesuisbenjamin on 2008-11-11
Oye Forum!

i'm trying to locate the folder wherein the icon (of Strange Quark in this case) used for the icon tray would be found.
Looking up for 'quark' in file system returns /usr/share/app-install/icons only, does this mean this is the only .png existing?

Thanks

---

### Post by ohzopants on 2008-11-14
Every item in your applications menu should have a *program_name*.desktop file associated to it.  The path for these escapes me at the moment.

If you open the .desktop file for that program in a text editor (or just cat it), it should have a line pointing you to the location of the icon.

---

### Post by brettnak on 2008-11-14
> **ohzopants said:**
> The path for these escapes me at the moment.

I think it's this in Hardy:
```
/usr/share/applications
```
Probably for Intrepid too, but I can't remember.

---

### Post by blackened on 2008-11-14
Looking at the source, it includes three tray icons: quark.png, quark32.png, and quark64.png. You might start by looking in /usr/share/pixmaps or (if it's there) the quark subfolder in /usr/share/pixmaps.

---

