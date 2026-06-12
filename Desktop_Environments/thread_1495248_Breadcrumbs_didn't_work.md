---
title: "Breadcrumbs didn't work"
date: 2010-05-27
forum: Desktop Environments
---

### Post by xdeathcorex on 2010-05-27
can someone show me how to fix this? i've done the making tweaks tab and now the breadcrumbs are still not showing.

here's the scrcap :

[IMG]http://img337.imageshack.us/img337/3361/screenshotlw.png[/IMG]

---

### Post by FatalChaos on 2010-05-27
Hey, make sure to restart nautilus or just restart your computer. Otherwise I don't think breadcrumbs kicks in until you do that.

---

### Post by xdeathcorex on 2010-05-27
Yeah already done that. So, do I need to reinstall it?

---

### Post by nilarimogard on 2010-05-28
How do you expect to have breadcrumbs if you use a text-mode location bar?

Use this:

gconftool-2 --type=Boolean --set /apps/nautilus/preferences/always_use_location_entry false

---

