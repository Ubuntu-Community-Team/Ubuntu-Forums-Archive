---
title: "Error when trying to install Beryl on Edgy, nVidia GeForce 7800 GT"
date: 2007-03-30
forum: Desktop Environments
---

### Post by Mugwump09 on 2007-03-30
I have the .tar extracted, and when I run the "sudo ./configure" command, it goes for a while but then it gives me this error, "checking for "xcomposite"... configure: error: xcomposite not found" HEP ME!

---

### Post by dbbolton on 2007-03-30
maybe your graphics card doesn't support compositing.

[quote=Brunellus]If beryl breaks, you get to keep both pieces.[/quote]

---

### Post by NikoC on 2007-03-31
Not sure if this may help but did you add the following lines at the end of xorg.conf?

Section "Extensions"
Option "Composite" "Enable"
EndSection

---

