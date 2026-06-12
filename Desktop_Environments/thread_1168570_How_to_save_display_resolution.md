---
title: "How to save display resolution"
date: 2009-05-24
forum: Desktop Environments
---

### Post by DavidTangye on 2009-05-24
I see that xorg.conf is now empty after installing Xubuntu. So the X server configuration is all derived on each startup. I guess this is a step forward.  However does anyone know how to save the display resolution for subsequent sessions if I make a change from the default, eg change 1366x1024 to 1152x720. I know I could add a modeline into xorg.conf, but repopulating xorg.conf seems retrograde. Also, it will lead to a question at upgrade time about 'replace, keep' etc the old file, which I try to minimise. I am hoping to be able to place a parameter into an Xubuntu desktop file, and perhaps on a per user basis, eg in $HOME/.(somewhere) would be ideal.

---

### Post by Legace on 2009-05-24
[https://wiki.ubuntu.com/X/Config/Resolution#Setting%20xrandr%20commands%20in%20.xprofile](https://wiki.ubuntu.com/X/Config/Resolution#Setting%20xrandr%20commands%20in%20.xprofile)

Maybe that?

---

