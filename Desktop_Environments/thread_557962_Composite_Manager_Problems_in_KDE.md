---
title: "Composite Manager Problems in KDE"
date: 2007-09-23
forum: Desktop Environments
---

### Post by Ice_Dragon on 2007-09-23
Every time I log into KDE,  two messages come up.  

"The Composite Manager crashed twice within a minute and is therefore disabled for this session."

"Composite extension not found
You must use XOrg &#8805; 6.8 for translucency and shadows to work.
Additionally, you need to add a new section to your X config file:
Section "Extensions"
Option "Composite" "Enable"
EndSection

This all started when I enabled transparency for the Crystal theme.  I disabled it and also uninstalled Compiz Fusion since I only used it in GNOME anyway, but it didn't help.  I tried editing the Xorg config file like the box said, but that messed up my desktop and made things really slow.  Any ideas?

---

### Post by Happy_Man on 2007-09-23
Are you using Feisty or better? That would solve the versioning problems.....

Do you have restricted drivers? That would make it so that the extension wouldn't crash....

Frankly, I hate KDE3's compositing. If you want it so bad, use Compiz Fusion until KDE4 gets out.

---

### Post by Ice_Dragon on 2007-09-23
I am using Feisty with the restricted ATI drivers.  It hasn't really affected anything that I can tell.  It's just annoying to have these messages come up every time I turn on the computer.

---

