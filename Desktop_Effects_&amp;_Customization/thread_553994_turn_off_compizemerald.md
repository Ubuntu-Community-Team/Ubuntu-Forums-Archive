---
title: "turn off compiz/emerald?"
date: 2007-09-18
forum: Desktop Effects &amp; Customization
---

### Post by Nythain on 2007-09-18
Is there a way to turn off compiz-fusion / emerald.
When i leave my computer for prolonged periods of time, it locks up... well it doesnt lock up, but i lose mouse and keyboard input, and the only way to fix it is to restart, but without a mouse and keyboard, the only way to do that is to hard power off it, wich = bad.

So i was thinking i could write the script to run it, then write a script to switch back to kwin when im away, but i dont know how to do this. In beryl it was easy, beryl-settings had a tray icon, i could click on it, select window manager, kwin... but i dont have this lovely tray icon with compiz fusion, and i know nothing about compiz fusion really... i start it with compiz --replace and i start emerald with emerald --replace...  woudl it truly be as simple as kwin --replace???

---

### Post by eoghanmurray on 2007-09-18
install the fusion-icon package.
Compiz Fusion has an icon that you can install.

[http://download.tuxfamily.org/shames/debian-sid/desktopfx/unstable/fusion-icon_0.1.1+git20070916-shame-0_i386.deb](http://download.tuxfamily.org/shames/debian-sid/desktopfx/unstable/fusion-icon_0.1.1+git20070916-shame-0_i386.deb)

---

### Post by Nythain on 2007-09-18
yeah, my computer didnt like that installation at all... any other ideas, i mean there has to be a command to turn off emerald and compiz

---

### Post by dondad on 2007-09-18
On my computer, the monitor will not shutdown when idle if compiz is running. I am running gnome, so I do alt-f2 and do metacity --replace. I don't know the equivalent for KDE or other desktops.

---

### Post by Nythain on 2007-09-18
should be kwin... guess i can give it a try... here's hoping for teh best

---

### Post by Nythain on 2007-09-18
holy sweet jesus it really is that simple... thanks for tellin me metacity --replace works

---

### Post by Nythain on 2007-09-18
bah, can never remember how to mark threads as solved, im such a retard

---

### Post by hyperair on 2007-09-18
For GNOME users metacity works too.

---

### Post by jazz452 on 2007-09-26
This kind of works but i play nexuiz quite alot and it will not run with compiz.Any other solutions,--replace option does not completely work you have to restart and guess what compiz starts again.The only way round i have found is to uninstall xgl everytime i want to play.Need start up session anybody.

---

### Post by hyperair on 2007-09-26
What graphics card are you using? If possible you should try to get rid of XGL completely (unless your system doesn't support AIGLX).

---

### Post by jazz452 on 2007-09-26
ati x1950 pro,It use to be very simple beryl had a login session as did gnome but now beryl   
and gnome share the same session.I can easily remove xgl but no desktop effects.If i have to make a choice nexuiz or compiz nexuiz wins.

---

