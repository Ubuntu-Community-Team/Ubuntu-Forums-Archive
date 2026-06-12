---
title: "Fast User Applet Issues"
date: 2008-10-10
forum: Desktop Environments
---

### Post by Keymaster on 2008-10-10
How can I disable the fast user switching applet?  It is presenting a problem as it tries to find the data on all my NIS users (100+ users) and thus lags the system when someone logs in. I already disabled gdmflexiserver by changing its permissions, but the fast user applet still works.  I went to Synaptic, but ubuntu-desktop depends on it (Shouldn't that be the reverse?)  Please help! Thanks

---

### Post by Ludwik on 2008-10-31
I had a very similar problem and I decided not to remove the applet, but instead change it's behavior to display only users that are currently logged-in on the machine.

You can set this for all users with the following command:

```
sudo gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.mandatory  --type bool  --set /apps/fast-user-switch-applet/show_active_users_only true
```

---

