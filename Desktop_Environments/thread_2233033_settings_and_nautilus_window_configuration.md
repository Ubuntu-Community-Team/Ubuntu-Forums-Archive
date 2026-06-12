---
title: "settings and nautilus window configuration"
date: 2014-07-05
forum: Desktop Environments
---

### Post by neba on 2014-07-05
Hello, 

I am running Ubuntu 14.04 and Gnome 3.12.1. Attached is a screen shot if my issue. I want to change Nautilus and Settings window configurations to look like all my other programs with a title bar on top and the close button on the left hand side. I have been looking around this past week and had no luck. Any help would be appreciated. 

R/S
Branden

[ATTACH=CONFIG]254506[/ATTACH]

---

### Post by mc4man on 2014-07-05
ubuntu patches nautilus for an ubuntu session to use the unity-window-deco. In a gnome session you'll get what the gnome devs want which is what you see.
Whether it's possibe to hack around that never tried as I use an ubuntu (unity) session

As far as the 'open dir. on dnd hover', I too find that obnoxious in icon view (dnd in a nautilus window
The other 3 ares are ok & at times useful.,  - sidebar, breadcrumbs, listview

Too that end I wrote a patch to revert in canvas view this behavior, you'd need to rebuild nautilus as it's not a config item, (though they could have made the timeout 'user adjustable' but those words are foreign in gnomeland

---

### Post by neba on 2014-07-06
I didn't know if there was a simple tweak that I could do Right now I don 't have the time to rebuild nautilus so I guess that I will have to live with it until Gnomeland becomes more user friendly. Thank you very much for your time.

R/ 
Branden

---

