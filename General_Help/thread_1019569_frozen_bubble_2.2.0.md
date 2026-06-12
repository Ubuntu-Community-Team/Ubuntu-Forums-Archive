---
title: "frozen bubble 2.2.0"
date: 2008-12-23
forum: General Help
---

### Post by Wartender on 2008-12-23
i have frozen bubble on my computer and i love it, but on their site i saw that they released version 2.2.0, while i have 2.1.0, is there any particular reason it isn't updating? (in synaptic frozen-bubble is there but only 2.1.0) i'm not too fond of compiling source code so... anybody know how i can update mine?

---

### Post by Titan8990 on 2008-12-23
Repositories will always be slightly behind actual releases. This because of the time that it takes to configure and create new .deb packages for everything in the repository when it gets updated.

If you are lacking a feature that the new version has, your only option is to install from a download directly from the publisher of the application.

If it does not lack features you can generally wait for it to hit the Ubuntu repositories without any issues.

---

### Post by mc4man on 2008-12-23
You won't see an updated version in hardy and probably not intrepid. The latest is in jaunty.
It's not that hard to build, only took about 2 min. though because there's no make uninstall I made a checkinstall .deb instead.

With checkinstall it installs to the default of /usr/local, which is no problem, if a menu item in games is wanted you just create one.

---

