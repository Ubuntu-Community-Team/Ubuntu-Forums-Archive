---
title: "No Compiz effects on Inspiron K/ubuntu 9.04 x64"
date: 2009-05-14
forum: General Help
---

### Post by frbe0101 on 2009-05-14
I did a compiz check and this what I got:

[SIZE="2"][I]Distribution:          Ubuntu 9.04
 Desktop environment:   KDE4
 Graphics chip:         Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 [COLOR="Red"]Checking for hardware/setup problems...           [WARN][/COLOR]

[COLOR="Red"]Something potential problematic has been detected with your setup:
 Warning: PCI ID 8086:2a02 detected.[/COLOR][/I][/SIZE]

I figure there is some kind of driver error, anyone got a solution?

---

### Post by frbe0101 on 2009-05-25
Can anyone help me here? It does not work in gnome either.

---

### Post by frbe0101 on 2009-05-25
Fix it no thanks to anyone here: :tongue:

graphics chip was blacklisted, had compiz skip the check:

echo "SKIP_CHECKS=yes" | sudo tee -a ~/.config/compiz/compiz-manager

---

