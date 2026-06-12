---
title: "xfce4-terminal using the generic window icon (Jaunty)"
date: 2009-04-24
forum: General Help
---

### Post by ldrn on 2009-04-24
Hopefully someone knows how to fix this, it's really irritating... I like using xfce's terminal, but with the latest release, it uses the generic window icon (like xterm) instead of the xfce4-terminal icon. I can assign the xfce4-terminal icon to the launcher manually, but the windows themselves still use the generic icon. Happens in both Gnome and XFCE.

*Edit* I was able to fix this by going to the /usr/share/icons/hicolor and /usr/share/icons/Human directories and running "sudo gtk-update-icon-cache --force ." in each.

---

