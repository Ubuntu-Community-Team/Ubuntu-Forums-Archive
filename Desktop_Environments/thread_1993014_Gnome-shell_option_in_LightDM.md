---
title: "Gnome-shell option in LightDM"
date: 2012-06-01
forum: Desktop Environments
---

### Post by DingusFett on 2012-06-01
I previously had gnome-shell installed, but removed it when I thought I'd stick with Unity. Now I've decided to give it another shot using some extensions, however I don't have the option for it when I log out and click the ubuntu logo to change DE. I have tried restarting to make sure it's nothing stupid like that. I have the option for GNOME Classic, and there is no gnome-shell.desktop file in /usr/share/xsessions

Does anybody have any ideas on how I can fix this? I'm new to Ubuntu/Linux, so not sure what to try from here.

---

### Post by sammiev on 2012-06-01
Just go into your Synaptic Package or what ever you may use and do a search under gnome. You will find the Desk top environment there. :)

---

### Post by DingusFett on 2012-06-01
I've tried reinstalled gnome-shell via both the Software Centre and Synaptic, with the same result.

---

### Post by Sularco on 2012-06-01
Package name is "gnome-shell". Pretty hefty download with all dependencies (170 MB if it was never installed). No further action needed, install package, log out, log back in and from the option next to the username/password login select gnome as your user-session.

---

### Post by sammiev on 2012-06-01
You can install with this as well.

```
sudo apt-get install gnome-shell
```

---

