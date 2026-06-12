---
title: "mucked up themes somehow"
date: 2007-10-16
forum: Desktop Environments
---

### Post by jessika-kaos on 2007-10-16
Somehow I seem to have broken the Gnome theme selector in Gutsy. I had installed a (single) theme into the /usr/share/themes directory to try to get synaptic to match up with everything else. It didn't work, so I then used gnome-theme-switcher, which worked once, then gave a segmentation fault after that.

now, when I select a theme with the normal theme switcher (which installed themes do not show up in), the buttons will change, but not the colors, and it seems pretty broken in general.

---

### Post by Neobuntu on 2007-10-16
I would try purging removing the themes that are not in the repositories, purge gtk-theme-switch and try the default theme to see if you can get things back under control.

Your problem might be related to the theme settings in /root too, as that's what is used for Synaptic.

---

### Post by jessika-kaos on 2007-10-16
I uninstalled everything except the default Human theme, and restarted, installed the gnome theme package, but the problem still persists. the icons and buttons can be changed, but the colors do not change with them.

---

### Post by jessika-kaos on 2007-10-16
Solved it. I had to edit the .gtkrc-2.0 file in /root to point to the default theme. Now after restarting X everything seems to be working.

---

