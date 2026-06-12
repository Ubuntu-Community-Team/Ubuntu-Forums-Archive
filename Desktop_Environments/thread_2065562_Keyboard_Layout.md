---
title: "Keyboard Layout"
date: 2012-10-02
forum: Desktop Environments
---

### Post by eaktivo on 2012-10-02
I have problem with keyboard layout "English (US), English (international AltGr dead keys)". I add it, and all works fine, but when i restart xubuntu 12.04 LTS keyboard layout "English (US), ..."  is missing and all keyboard layout settings is set to default. 

I need two keyboard layouts: SK, EN (US), but after restart only SK is available. EN not present. 

All parameters about keyboard layout works fine, until i restart xubuntu. After restart - all parameters about keyboard layout is set to  defaults.

How to add English (US) keyboard layout permanently and all settings about it ?

---

### Post by LewisTM on 2012-10-02
How do you manage your keyboard layouts? Do you use the Xkb panel plugin? If not, you should. And set the Xfce keyboard settings to use System defaults to avoid conflicts.

Cheers!

---

### Post by eaktivo on 2012-10-02
> **LewisTM said:**
> How do you manage your keyboard layouts? Do you use the Xkb panel plugin? If not, you should. And set the Xfce keyboard settings to use System defaults to avoid conflicts.

Cheers!

yes, i use standard keyboard layout plugin installed with Xubuntu 12.04  LTS (same as on picture:  [http://goodies.xfce.org/projects/panel-plugins/xfce4-xkb-plugin](http://goodies.xfce.org/projects/panel-plugins/xfce4-xkb-plugin)).

I set some settings like on picture ([http://goodies.xfce.org/_media/projects/panel-plugins/xfce4-xkb-plugin-0.5.3-settings.png?cache=](http://goodies.xfce.org/_media/projects/panel-plugins/xfce4-xkb-plugin-0.5.3-settings.png?cache=)), but after restart xubuntu all settings is default and other keyboard layouts is missing.

---

### Post by LewisTM on 2012-10-02
That's a common bug, the plugin crashes and nobody seems to be able to fix it. Did you set your Xfce Keyboard Settings (in Settings Manager) to use System Defaults? Anything else will cause problems.

---

### Post by eaktivo on 2012-10-09
> **LewisTM said:**
> That's a common bug, the plugin crashes and nobody seems to be able to fix it. Did you set your Xfce Keyboard Settings (in Settings Manager) to use System Defaults? Anything else will cause problems.

Yes, i set it. If i open Xfce Keyboard Settings (in Settings Manager) - plugin start and all keyboard layouts show on panel, but shortcut keys for change keyboard layout is set to "none" (i always need to setup it back to ALT+SHIFT, as before). Same settings not stored.

---

