---
title: "Setting environment variables in the Gnome desktop"
date: 2009-10-23
forum: Desktop Environments
---

### Post by rfritz on 2009-10-23
They are set in the .gnomerc file.

Some technical notes:
[LIST]
[*] .gnomerc is read in /etc/X11/Xsession.d/55gnome-session_gnomerc. 
[*] An "sh" shell is used
[*] "source ~/.env_vars" will *not* work; use ". $HOME/.env_vars" instead
[/LIST]

---

