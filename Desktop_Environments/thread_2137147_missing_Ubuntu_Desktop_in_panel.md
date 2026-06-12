---
title: "missing Ubuntu Desktop in panel"
date: 2013-04-19
forum: Desktop Environments
---

### Post by jwyman on 2013-04-19
when I log in to my system ( version 12.04) as the default user, I see the title "Ubuntu Desktop" initially on the left side of the panel at the top of my screen along with some menus that I can access, but when I log in through my primary account, which I have done a lot of customizations to, the panel just stays blank up there, even though other programs I run are able to display their titles and menus in that panel area, so I am just trying to figure out what module specifically in Unity or whatever is responsible for that "Ubuntu Desktop" title and narrow down my search for the changes  to my configuration settings may have caused this difference in behavior between the two accounts --- thanks in advance for any help

---

### Post by stinkeye on 2013-04-19
If you have disabled nautilus handling the desktop you won't see "Ubuntu Desktop" when viewing the desktop.

Check your setting via terminal....
```
gsettings get org.gnome.desktop.background show-desktop-icons
```

Reset to default (true)...
```
gsettings reset org.gnome.desktop.background show-desktop-icons
```

---

