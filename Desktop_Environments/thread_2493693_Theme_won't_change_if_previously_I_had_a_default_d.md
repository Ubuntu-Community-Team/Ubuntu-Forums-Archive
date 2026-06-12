---
title: "Theme won't change if previously I had a default dark ubuntu theme"
date: 2023-12-21
forum: Desktop Environments
---

### Post by limce on 2023-12-21
Not long ago I changed my ubuntu theme and all have been working until now. So now when I log in my dock is white, but dark theme is turned on. Also some windows remains white. I am trying to change all themes to black but it wont work properly or wont work at all. There is 2 cases. 
1. If I turn on an any default light ubuntu theme in settings then I can change it to any theme I would want. But if it is dark theme I changing into then some windows/application remain white and my dock change it's color to white after reload.
2. If I turn on an any default dark ubuntu theme in settings then I can't even change it. No matter what theme I chose it wont change.

And as you can see in my attached file there is one more issue with dock. When I click "Show Applications" second dock appears. And it is fully functional.
I also attached image with my tweaks and extension manager settings.

---

### Post by Dennis N on 2023-12-21
You don't mention what Ubuntu release you are using, so here's a few general remarks. Applications installed as snap and flatpak don't always have access to the same themes as those installed from .deb packages. That may be one factor here. Try using only **Adwaita** or **Adwaita Dark** application theme. That should offer uniformity.

Themes installed from an outside source (like gnome-look.org) may be old and incompatible with new application builds,  or incompatible for other reasons.

If you have a recent gnome-shell version, like 43,44,45 then gnome applications (like Files, for example) might use libadwaita and gtk4. These don't use any installed theme at all. So your theme choice would have no effect.

As for the superimposed docks. I can't get that to happen, so no explanation.

---

