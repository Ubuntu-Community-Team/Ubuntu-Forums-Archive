---
title: "Backlight + Lock on a notebook"
date: 2006-06-05
forum: Desktop Environments
---

### Post by raghav_p on 2006-06-05
In Hoary and Breezy I used the following in a script to turn off the backlight and activate the screensaver lock on my notebook:

```

xset dpms force standby
xscreensaver-command -activate
xscreensaver-command -lock

```

In Dapper, this no longer works, presumably because Dapper uses gnome-screensaver? I couldn't find anything in the manpages about this so is there anyway to tell gnome-screensaver to activate and lock? Thanks!

---

