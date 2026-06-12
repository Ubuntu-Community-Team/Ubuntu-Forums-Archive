---
title: "Can't access panel properties"
date: 2007-12-23
forum: Desktop Environments
---

### Post by purplenite on 2007-12-23
When I right-click on my panels I only get two options in the menu, Help and About Panels. The normal options like Properties, New Panel, etc. have disappeared.

The issue began after I changed the minimized panel size from 6 to 0 in gconf-editor, but changing the value back to 6 doesn't solve the problem.

Any suggestions?

---

### Post by scorcher on 2007-12-27
I think you accidentally locked down your panel.

Locking down the panel makes it so you cannot move your panel or change any of its settings. That is why you cannot access any of the options in the right-click menu.

The setting is located in gconf-editor at:
/apps/panel/global/locked_down

---

