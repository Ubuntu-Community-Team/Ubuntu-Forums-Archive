---
title: "unresponsive pointer in firefox"
date: 2012-01-15
forum: Desktop Environments
---

### Post by margu on 2012-01-15
I have the same problem on my both of my computer with 11.10. The pointer sometimes becomes unresponsive when jusing firefox. It usually happens after a few seconds of using firefox. I use ctrl+alt+del to log off and then login and try again. Please help.

---

### Post by Krytarik on 2012-01-15
Try running Firefox with all add-ons disabled first, to exclude any conflicting ones:

[LIST]
[*]GUI (if possible): "Help -> Restart with Add-ons Disabled"
[*]command line: "firefox -safe-mode"
[/LIST]
If that helps, you obviously need to figure out which specific add-on is the culprit.

If that doesn't help, I'd just rename the profile directory under "~/.mozilla/firefox", usually named like "xxx.default", to exclude anything faulty inside there.

Hope any of this works out.

---

### Post by margu on 2012-02-02
It seems to be a usual problem and the remedy is to deselect "Disable touchpad while typing" in the system setting. After this, I h<ve not had any problems at all.

---

