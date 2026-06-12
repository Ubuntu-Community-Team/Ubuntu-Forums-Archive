---
title: "GTK-fonts blurred"
date: 2008-11-12
forum: Desktop Environments
---

### Post by Bendemann on 2008-11-12
I enabled font antialiasing in system control. KDE-apps are fine but each GTK-program (like Firefox, Avidemux) has blurred fonts. It seems that antialiasing isn't working here.

I'm using Tahoma, installed gtk-qt-engine-kde4 and gtk-qt-engine and made also a dpkg-reconfigure fontconfig-config.

---

### Post by aged hippy on 2008-11-12
You could also try adjusting them on the *Configure* tab.

Also, maybe try enabling the box below it: *Force fonts DPI:*

I've set mine to 120, and they are crisp and clear.
(Microsoft Comic Sans.)

---

### Post by Bendemann on 2008-11-12
Thanks, I already did. Each change affects KDE but not GTK.

---

### Post by aged hippy on 2008-11-12
Under *->System Settings ->Appearance ->GTK Styles and fonts* have you told it to use yours, or another.... whichever it is now, try changing it. 

It will require a log-out (and in again :)) to take effect.

---

