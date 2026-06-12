---
title: "&quot;Allow Launching&quot; of desktop icons through CLI"
date: 2019-05-10
forum: Desktop Environments
---

### Post by apwhawkins on 2019-05-10
Hi,

I'm pushing out a couple of desktop icons to ubuntu machines through ansible

```
#!/usr/bin/env xdg-open

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon[en_GB]=gnome-panel-launcher
Name[en_GB]=officecam
Exec=**payload**
Name=officecam
Icon=/usr/share/vlc/lua/http/favicon.ico


```

After a do-release-upgrade ( to 19.04, nautilus 3.32) I'm finding I have to manually right click and "Allow Launching" and was hoping this was a change I could scripts to save the manual interaction?

What setting is this changing?

---

### Post by mc4man on 2019-05-10
There is no setting, this is the way nautilus works now..
You could set another file-manager to run the Desktop, most compatible is nemo. 
While in a unity session this switch is automatically done it would require a little work to do so in a gnome session.

---

### Post by apwhawkins on 2019-05-28
Sorry, I'd missed this reply. 

A shame but thanks for coming back to me, much appreciated!

---

