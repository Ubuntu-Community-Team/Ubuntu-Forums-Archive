---
title: "[urgent] Xfce panel is gone"
date: 2011-02-09
forum: Desktop Environments
---

### Post by Terryracoon on 2011-02-09
So... I was ******* around with wine, and when i tried to run a certain game.... The xfce panel vanished! It's simply gone! Rebooting didn't help.... And when i tried running it from a terminal i got this:
> /usr/share/themes/Murrine-Sky/gtk-2.0/gtkrc:45: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/Murrine-Sky/gtk-2.0/gtkrc:51: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/Murrine-Sky/gtk-2.0/gtkrc:54: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/Murrine-Sky/gtk-2.0/gtkrc:45: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/Murrine-Sky/gtk-2.0/gtkrc:51: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/Murrine-Sky/gtk-2.0/gtkrc:54: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/Murrine-Sky/gtk-2.0/gtkrc:45: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/Murrine-Sky/gtk-2.0/gtkrc:51: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/Murrine-Sky/gtk-2.0/gtkrc:54: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/Murrine-Sky/gtk-2.0/gtkrc:45: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/Murrine-Sky/gtk-2.0/gtkrc:51: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/Murrine-Sky/gtk-2.0/gtkrc:54: Murrine configuration option "gradients" is no longer supported and will be ignored.
Exceção de ponto flutuante (floating point exception?)
EDIT: Turns out if you insist (as in, keep on entering the same command repeatedly) i could actually get it to work, but whenever i log out it goes away again!

---

### Post by 3Miro on 2011-02-09
It seems like you are using an outdated/unsupported/incompatible theme. Murrine is a "gtk-engine", meaning it is responsible for drawing colorful panels, decorations and effects. XFCE has some issues with GTK themes, if those are designed for Gnome specifically. Try using a different theme.

---

