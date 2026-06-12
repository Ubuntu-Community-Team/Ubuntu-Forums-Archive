---
title: "[xubuntu] panel-launcher-tooltips are tiny now, can't increase size"
date: 2018-10-21
forum: Desktop Environments
---

### Post by Moses_Moore on 2018-10-21
After the upgrade from Xubuntu 18.04 to 18.10, the XFCE4 panel launcher widgets are tiny (16x16), and I'm unable to increase their size.  They were 32x32 while I was using Xubuntu 18.04.

According to [https://docs.xfce.org/xfce/xfce4-panel/launcher](https://docs.xfce.org/xfce/xfce4-panel/launcher), it says:

> [COLOR=#000000][FONT=&amp]You can set a custom menu and tooltip icon size in gtk-icon-sizes with the name [/FONT][/COLOR]panel-launcher-menu[COLOR=#000000][FONT=&amp] and [/FONT][/COLOR]panel-launcher-tooltip[COLOR=#000000][FONT=&amp]. The default icon sizes are both 32px. 

[/FONT][/COLOR]But there is no program named "gtk-icon-sizes" nor a software package named "gtk-icon-sizes" nor "xfce4-gtk-icon-sizes".

I thought maybe it was a setting in ~/.gtkrc-2.0 , but i tried adding this line to the file and reloading xfce4-panel :

> gtk-icon-sizes="[COLOR=#000000][FONT=monospace]panel-launcher-menu=32,32:[/FONT][/COLOR]panel-launcher-tooltip=32,32"

And it had no effect.  I also tried opening `xfce4-settings-editor` going to xsettings > Gtk > IconSizes and adding "panel-launcher-tooltip=32,32" and reloading, but that also had no effect.

I'm not sure what else to do.  The instructions "in gtk-icon-sizes" is unclear.

---

### Post by again? on 2018-10-21
Test a new user account.

---

### Post by Moses_Moore on 2018-10-23
Tested.  new account, empty $HOME/ and the problem is still there.  Following up at the xfce4 forums, seems the problem is when XFCE is offered GTK3 instead of GTK2.

---

