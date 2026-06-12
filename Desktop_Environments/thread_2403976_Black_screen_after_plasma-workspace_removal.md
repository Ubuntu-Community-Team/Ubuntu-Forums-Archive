---
title: "Black screen after plasma-workspace removal"
date: 2018-10-18
forum: Desktop Environments
---

### Post by chriswyatt on 2018-10-18
The upgrade from Lubuntu 18.04 to 18.10 left quite a bit of left over baggage. I've been removing some of it. I uninstalled plasma-workspace and used ```
autoremove --purge
``` to get rid of the dependencies; however my system became unbootable. Reinstalling plasma-workspace fixed the issue.

Well, the system reached the login screen, but if I clicked anywhere on the login screen, the screen would turn black, apart from the mouse cursor.

Is this a bug in the dependency tree? Should lubuntu-desktop depend on plasma-workspace?

Also, I've been trying to figure out what installed plasma-workspace in the first place, and thought it was perhaps a 'recommends' dependency from another package; however I haven't had much luck finding anything using 'apt-cache depends', and I'm not too familiar with the magic behind apt and distribution upgrades.

Can anyone enlighten me? Even if it's not a bug, I'd still be curious how plasma-workspace relates to LXQt, and whether I actually need plasma-workspace, or just one of its dependencies.

---

### Post by Claus7 on 2018-10-19
Hello,

have you tried Ctrl+Alt+F#, where # is any number on your keyboard?
It seems to be a graphics driver problem.

Regards!

---

