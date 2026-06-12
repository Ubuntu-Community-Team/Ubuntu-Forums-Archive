---
title: "What package is responsible for displaying available login sessions?"
date: 2014-06-17
forum: Desktop Environments
---

### Post by kansasnoob on 2014-06-17
I need to file a bug report because Ubuntu GNOME displays the GNOME Flashback (Compiz) session even when 'compiz' is not installed.

It's not just a 'gdm' thing because that session appears also with 'lightdm' regardless of which greeter is used.

I suppose I could just file the bug against 'gnome-session-flashback' but it seems more appropriate to file it against whatever package actually manages sessions ;)

---

### Post by steeldriver on 2014-06-17
I've always thought that (at least for lightdm) it just presents everything for which it finds a corresponding .desktop file in /usr/share/xsessions - so it's up to the session package to make sure it cleans up its .desktop files when it is removed.

---

### Post by kansasnoob on 2014-06-19
> **steeldriver said:**
> I've always thought that (at least for lightdm) it just presents everything for which it finds a corresponding .desktop file in /usr/share/xsessions - so it's up to the session package to make sure it cleans up its .desktop files when it is removed.

That makes sense. I filed a bug report:

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1332183](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1332183)

Many thanks.

---

