---
title: "Compiz window decorations tip after Gutsy upgrade"
date: 2007-10-21
forum: Desktop Effects &amp; Customization
---

### Post by Despot on 2007-10-21
I hope I'm not posting old info here, but I wanted to pass this along in case it'd save somebody the headaches I dealt with to get Compiz working after upgrading to Gutsy.

Upgraded to Gutsy. Had troubles with Compiz, so removed/reinstalled (I'd been using the tuxfamily.org repo). Window decorations disappeared after a reboot. The fix was to remove the ~/.config/compiz/compizconfig/ directory (which hadn't been removed in the reinstall of Compiz, although I'm next to positive I did a 'Complete Removal' of the packages involved).

Moral of the story, user config files from 'other' packages can mess with Compiz, and aren't necessarily purged when the packages are uninstalled. It'd be nice to have an option in Compiz along the lines of 'Reset user settings to default' for such cases...

---

