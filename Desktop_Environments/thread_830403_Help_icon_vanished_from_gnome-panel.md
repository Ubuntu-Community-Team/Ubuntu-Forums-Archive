---
title: "Help icon vanished from gnome-panel"
date: 2008-06-15
forum: Desktop Environments
---

### Post by Mike Brennan on 2008-06-15
While I was rearranging some icons on my gnome-panel, the help icon (for gnome-help) vanished. I did not remove it, but I did unlock it and was dragging it to a new location when it simply vanished.

If I select "Add to panel", "help" is not there as an option. Presumably, I could create a custom application launcher for it, but then I have to select a custom icon and don't just get the default help icon.

I tried removing the ~/.config/menus directory, then logging out and logging back in hoping that gnome-panel would simply revert to its default layout, but it didn't.

If I right-click on the gnome panel, "Help" shows up in the context menu and launches fine. Is there a way to get the icon back in the panel, though?

Thanks.

---

### Post by Vadi on 2008-06-15
You can use this for the help icon: "/usr/share/icons/Human/48x48/apps/gnome-help.png"

As for getting it back, I'm not sure how, it looks like ubuntu sets the custom launcher for you and it's not an applet.

---

### Post by vrezic on 2008-12-08
Right click with mouse then choose Add to Panel
Custom Application Launcher then Add

Name: Help
Command: yelp
Comment: Get help with Ubuntu

Hope this can help someone.

Veselin Rezic

---

