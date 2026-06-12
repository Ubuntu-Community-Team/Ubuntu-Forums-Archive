---
title: "Window Maker &amp; Gnome problem"
date: 2006-02-21
forum: Desktop Environments
---

### Post by FIONEX on 2006-02-21
Greetings everyone!
I've installed Window Maker and Gnome but the problem is that certain applications make a little box at the bottom of the screen, not just when they're minimized.  For example, FireFox and GAIM.  They really clutter the work space :S.  How do I get rid of them ??

---

### Post by FIONEX on 2006-02-21
I've figured something out, not sure if it's the right way because I made it up myself.  But if anyone cares for a solution to the AppIcon problem, then they should open ~/GNUstep/Defaults/WMWindowAttributes and add the following few lines:
```

  "*" = {
    NoAppIcon = Yes;
    Icon = defaultAppIcon.tiff;
  };
  DockApp = {
    NoAppIcon = No;
  };

```

The essential part there is the NoAppIcon = Yes; under the "*" category which applies to all windows.  By Adding the DockApp category, this allos app icons for dock apps!

Hopefully this is a usefull contribution to some people.

---

