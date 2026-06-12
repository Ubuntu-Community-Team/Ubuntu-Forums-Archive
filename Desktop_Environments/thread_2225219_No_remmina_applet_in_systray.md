---
title: "No remmina applet in systray"
date: 2014-05-20
forum: Desktop Environments
---

### Post by korb on 2014-05-20
After upgrading to 14.04 LTS trusty and installing GNOME shell my remmina AppIndicator in the systray was missing. I googled and didn't find a solution. I did find a post whereby the Network Manager applet wasn't showing up. The solution for that was to start it with dbus-launch, and that exact same solution resolves the missing remmina systray applet.

```
dbus-launch remmina -i
```

(you can leave off the "-i" if you don't want to start iconified).

Note that you will want to add this to your Startup Applications if you use remmina on a regular basis. You may also want to change the remmina menu item properties to do the same if you prefer to start remmina from your Applications menu.

---

