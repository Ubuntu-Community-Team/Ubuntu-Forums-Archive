---
title: "files in .config/autostart visible with startup manager but not being executed (9.10)"
date: 2009-12-09
forum: Desktop Environments
---

### Post by jtprince on 2009-12-09
I have some files (soft-links really) in my ~/.config/autostart folder that I want executed when I login.  They were executed just fine in previous versions of Ubuntu but not so with 9.10.  Any idea what is going on here?  

```
[Desktop Entry]
Type=Application
Name=XBindKeys
Exec=xbindkeys
Icon=system-run
Comment=
Name[en_US]=XBindKeys
Comment[en_US]=
X-GNOME-Autostart-enabled=true

```

The files are picked up properly by System->Preferences->Startup Applications and appear to be properly formatted, they just do not seem to be executed.  I have no problems executing the commands in a terminal.

Very mysterious.

---

### Post by whyohwhy on 2009-12-15
I got the same problem. Ubuntu 9.10.  The problem occurred right after I did a Nvidia kernel upgrade.  I don't believe it is a permissions setting.

---

### Post by wizel on 2009-12-19
Same here.
file is there with proper content, but doesn't start after loging.

---

