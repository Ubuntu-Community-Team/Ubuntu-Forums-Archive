---
title: "Unity - how to make double click title bar action maximize VERTICALLY?"
date: 2012-07-23
forum: Desktop Environments
---

### Post by entropy1 on 2012-07-23
When using the old Gnome desktop, I could configure window behavior so that double clicking on the title bar would maximize vertically.  But I can't figure out how to do that with Unity.  Does anyone know how?

---

### Post by Krytarik on 2012-07-23
This should work - tried already?:
```
gconftool-2 --set --type string /apps/metacity/general/action_double_click_titlebar toggle_maximize_vertically
```Note: The default setting is "toggle_maximize".

Regards.

---

### Post by entropy1 on 2012-07-23
Thank you for the suggestion, Krytarik.  Unfortunately, it has no effect.  After issuing the command, double clicking the title bar maximizes to the entire screen.

---

### Post by rehdwolfe on 2012-08-02
I am able to make this work with Unity .


[LIST]
[*]    Install the gconf-editor.
[LIST]
[*]    (sudo -s apt-get install gconf-editor)
[/LIST]
[*]    Navigate to app>metacity>general>action_double_click_titlebar and change the value to toggle_shade
[*]    Enjoy
[/LIST]
See attached jpeg

---

### Post by entropy1 on 2012-08-02
rehdwolfe,

That makes the window roll up, but leaves the title bar.  It does not make the window maximize vertically from the top of the screen to the bottom.

---

### Post by markbl on 2012-08-02
I use gnome-shell rather than unity but gnome-tweak-tool has an option under the windows settings where you can set this action. Works in gnome-shell, does it work in Unity?

---

### Post by entropy1 on 2012-08-02
markbl,

Yes, it works in gnome shell, but not in unity or in gnome-no effects.  However, if I install cinnamon and use cinnamon-settings to set windows to maximize vertically, then I get this behavior in gnome-no effects too.

---

### Post by Krytarik on 2012-08-03
Incited by the recent activity on this thread, I've investigated that matter thoroughly earlier today, and it became clear that the current version of Compiz doesn't respect the options "toggle_maximize_vertically" and "toggle_maximize_horizontally" for the Metacity settings "action_double_click_titlebar" and "action_middle_click_titlebar", while they work fine in Metacity itself. Instead, Compiz would just apply the default action for either of those settings, which is "toggle_maximize" for the former, and "lower" for the latter.

There is apparently no Compiz setting to change that behavior, neither found one in CompizConfig Settings Manager, nor in GConf. Afaik, the only viable workarounds for that, as of now, would be to use middle-click on the 'Maximize' window control button, or set up a key combination for that under "CCSM -> General Options -> Key Bindings".

It seems like there hasn't been filed a bug report reg. that already, so if inclined to that extent, you can do that here:

[https://bugs.launchpad.net/ubuntu/+source/compiz](https://bugs.launchpad.net/ubuntu/+source/compiz)

Regards.

---

### Post by entropy1 on 2012-08-03
Krytarik,

Thank you for looking into this.  I used your suggestion to set up a key combination under "CCSM -> General Options -> Key Bindings".  Now <control>v does what I want :)

---

