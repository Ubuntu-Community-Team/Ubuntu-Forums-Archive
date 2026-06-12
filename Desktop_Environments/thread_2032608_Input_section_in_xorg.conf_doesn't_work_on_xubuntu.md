---
title: "Input section in xorg.conf doesn't work on xubuntu"
date: 2012-07-24
forum: Desktop Environments
---

### Post by Miarld on 2012-07-24
Hi all

I've changed my xorg.conf but nothing seems to happen after reboot.
What have I done wrong?

```

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us,he,ru,dvorak"
	Option	    "XkbOptions" "grp:caps_toggle"
EndSection


```

---

### Post by LewisTM on 2012-07-24
In Xubuntu one configures the keyboard through the Xkb panel plugin, found in the xfce4-goodies metapackage or in xfce4-xkb-plugin.

Just add it to one of you panels and configure the keyboard options. 

Also make sure system defaults are selected in the Settings Manager/Keyboard/Layout section since anything else will conflict with the plugin. It would be safer to remove your xorg.conf options for the same reason.

Cheers!

---

### Post by Miarld on 2012-07-29
Thank you, it works.

---

