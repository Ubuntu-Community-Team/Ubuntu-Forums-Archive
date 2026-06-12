---
title: "where is gnome startup program config"
date: 2005-07-14
forum: Desktop Environments
---

### Post by usergentoo on 2005-07-14
How to  System->Preferences->Sessions->Startup Programs add a program without a gui.

I have a small server and I want to add a startup program to it and was told to go the above to do it.Is there a way to do it in terminal without a gui. This server is headless and I connect through it using ssh.

---

### Post by badrinarayan on 2005-07-14
Edit [FONT=Courier New]~/.gnome2/session-manual[/FONT] for local changes or [FONT=Courier New]/usr/share/gnome/default.session[/FONT] for global changes

[FONT=Courier New]man default.session[/FONT] for documentation

Regards
Badri

---

