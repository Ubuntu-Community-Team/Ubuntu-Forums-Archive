---
title: "kdm fails to load at boot"
date: 2006-07-18
forum: Desktop Environments
---

### Post by rosslaird on 2006-07-18
I recently switched (as I often do) back to kde from gnome, and ran dpkg-reconfigure gdm to switch the login manager to kdm. I got some type of error, which I can't reproduce and can't recall, but the upshot is that while kdm works (if I run it a console, using /etc/init.d/kdm start), and kde runs fine, kdm will not start at boot. It does not even show up in rcconf.

Hm. Suggestions most welcome.

Ross

---

### Post by snaga on 2006-07-18
I also have this problem. It started when I upgraded to Dapper. I don't have a resolution. Others have said the switching to GDM worked for them. I haven't tried that yet. Currently I am booting to command line and running kdm by hand, as it sounds like you are.

I don't reboot very often, so fixing it hasn't been a high priority.

---

### Post by rosslaird on 2006-07-19
I changed back to gdm (using dpkg-reconfigure) and I received what I think is the same error message with kdm:

```
grep: /etc/X11/default-display-manager: No such file or directory
 * Reloading GNOME Display Manager configuration...  * Changes will take effect when all current X sessions have ended.
invoke-rc.d: initscript gdm, action "reload" failed.
Cannot open file /etc/X11/mwm//system.mwmrc-menu.

install-menu: /etc/menu-methods/motif-clients: aborting
update-menus[11611]: Script /etc/menu-methods/motif-clients returned error status 1
```

When I run update-menus, I get the error again. So, I think that's where the problem is. No solution yet, though.

---

