---
title: "Can't remove icon in panel"
date: 2010-01-07
forum: Desktop Environments
---

### Post by keta on 2010-01-07
While I was looking for a solution over an issue I had with the login screen, I came up the command I found in the following page: [http://gnome-look.org/knowledgebase/?id=274](http://gnome-look.org/knowledgebase/?id=274)

```
gksudo -u gdm dbus-launch gnome-appearance-properties
```When I run the command, two new icons appeared on the panel, which when clicked showed up some assistive options (enhance contrast, make text larger and so on, you can see what I mean in the attached image).

I managed to remove one of the icons with a simple right-click, but the other one stays there. Clicking opens up the window shown in the attached image, right-clicking does nothing. I restored the panels to the original settings, but it continues there!

Any idea on how to get rid of this? Any help is appreciated! :)

---

### Post by mcduck on 2010-01-07
Go to System/Preferences/Keyboard, and on the Accessibility-tab disable the "Accessibility features can be toggles with keyboard shortcuts"-option.

---

### Post by keta on 2010-01-07
THANKS!! That made it :D

---

