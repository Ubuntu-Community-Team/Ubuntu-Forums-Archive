---
title: "different wallpapers on different workspaces?"
date: 2009-12-04
forum: Desktop Environments
---

### Post by calwyn on 2009-12-04
I haven't been using Ubuntu for very long and I just found the marvel that is Compiz, which lets you form your workspaces into a cube. I'm wondering if its possible to have a different wallpaper on each workspace. That would make it easier for me to keep track of where my stuff is since I usually work with windows minimized on each workspace I'm not currently using. I'm running Ubuntu 9.10.

---

### Post by chickengirl on 2009-12-04
> **calwyn said:**
> I haven't been using Ubuntu for very long and I just found the marvel that is Compiz, which lets you form your workspaces into a cube. I'm wondering if its possible to have a different wallpaper on each workspace. That would make it easier for me to keep track of where my stuff is since I usually work with windows minimized on each workspace I'm not currently using. I'm running Ubuntu 9.10.

From what I've heard, yes. I haven't used Compiz in a while though, so I couldn't tell you how.

---

### Post by carlinuxlearner on 2009-12-05
@calwyn

Yes it is possible (and quite easy), but it will disable your desktop icons/shortcuts.

If you want to try it, here's the info.

1. In the terminal paste this: ```
gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop false
```

2. Assuming you've installed the "CompizConfig Settings Manager", open it up (Located on the menu here: System>>Preferences>>CompizConfig Settings Manager), go to the "wallpaper" plug-in check-mark it, then set your backgrounds.

2.1 If you haven't installed "CompizConfig Settings Manager", open up a terminal and paste this: ```
sudo apt-get install compizconfig-settings-manager
```
Then follow step 2.

---

### Post by MarcusA on 2009-12-05
Would this be possible using KDE and keeping your icons since its a bit different?

---

### Post by carlinuxlearner on 2009-12-07
Yes, in KDE you can keep your icons and select different wallpapers for each workspace.

---

