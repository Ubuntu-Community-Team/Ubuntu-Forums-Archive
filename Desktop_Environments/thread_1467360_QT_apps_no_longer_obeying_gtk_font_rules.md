---
title: "QT apps no longer obeying gtk font rules"
date: 2010-04-30
forum: Desktop Environments
---

### Post by Compintuit on 2010-04-30
I just installed lucid over karmic, with a separate /home, and now all of my qt apps, though still obeying the other gtk options, preform font smoothing; I have it set to have none, as that looks best on my monitor. Has anyone else experienced this problem? Fixed it? Thanks.

Edit: I've managed to fix this, by installing kde's systemsettings module. I set antialiasing to disabled instead of default, and uninstalled all the kde stuff it pulled in after. Still don't know wherer the setting is, which is buggin me. I don't think it's under .local, .cache, .config, or .gconf as I tested with empty ones.

---

