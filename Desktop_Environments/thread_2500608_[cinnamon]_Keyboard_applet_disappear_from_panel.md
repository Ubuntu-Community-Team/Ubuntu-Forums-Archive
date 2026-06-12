---
title: "[cinnamon] Keyboard applet disappear from panel"
date: 2024-09-06
forum: Desktop Environments
---

### Post by dclabaut on 2024-09-06
Hello,

I have found an issue where the Keyboard applet in Cinnamon on Ubuntu (base install is Ubuntu Server with Gnome) disappears from the panel, and can only be re-added by changing the order of layouts in the Keyboard settings menu.

The issue has been reproduced on 2 machines with very different hardware, one runs Ubuntu 22 with Cinnamon 5.2.7-4 and the other runs Ubuntu 24 with Cinnamon 6.0.4-4

Step-by-step:
- In keyboard settings, add a second layout (or the applet to switch does not appear, which is fair)
- right-click the Cinnamon panel, click Applets, then add the Keyboard applet. The applets appears.
- After a while the Applet disappears.
- Right-click the panel to enable Panel Edit Mode shows the icon for the Keyboard applet.
- Right-click the panel to disable Panel Edit Mode removes said icon.
- In Keyboard Settings, moving the layouts in the list triggers the appearance of the applet
- Go do something else then the applet disappears

Immediately after moving the layouts in the listm the following appears in journalctl, repeated about 10 times in 3 seconds:
sep 06 11:43:08 redacted cinnamon[5058]: xapp_kbd_layout_controller_get_current_group: assertion 'controller->priv->enabled' failed
sep 06 11:43:08 redacted cinnamon[5058]: JS ERROR: TypeError: item is undefined
                                             [email]_syncGroup@/usr/share/cinnamon/applets/keyboard@cinnamon.org/applet.js[/email]:281:9

---

