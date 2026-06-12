---
title: "missing key sleep-display-ac in gnome-settings-daemon-schemas"
date: 2014-09-27
forum: Desktop Environments
---

### Post by nhanth87 on 2014-09-27
hi,
today I check 
[http://bazaar.launchpad.net/~ubuntu-branches/ubuntu/utopic/gnome-settings-daemon/utopic/view/head:/data/org.gnome.settings-daemon.plugins.power.gschema.xml.in.in](http://bazaar.launchpad.net/~ubuntu-branches/ubuntu/utopic/gnome-settings-daemon/utopic/view/head:/data/org.gnome.settings-daemon.plugins.power.gschema.xml.in.in)

and found there's no sleep-display-ac.
Without this key, I cant set display timeout. Anyone have ideas please help? :(

---

### Post by CantankRus on 2014-09-28
Use **sleep-inactive-ac-timeout**
eg
```
gsettings set org.gnome.settings-daemon.plugins.power sleep-inactive-ac-timeout  300
```

---

### Post by nhanth87 on 2014-09-28
Hi cantankRus,
Thank for your reply but I just want to sleep my display not the hole system :)

---

