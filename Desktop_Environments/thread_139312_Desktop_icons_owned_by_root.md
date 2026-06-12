---
title: "Desktop icons owned by root"
date: 2006-03-03
forum: Desktop Environments
---

### Post by jabowery on 2006-03-03
Since the Debian package for ejabberd is running so far behind and the current linux installer.bin for ejabberd is their 1.0.0 release, I went ahead and used that to install ejabberd.

This however created some ejabberd start/stop icons on my desktop which have a tiny lock sub-icon, and when I click them it complains I don't have sufficient privileges to run those programs.

Can I switch to root to run the icons on my desktop or do I have to find the command to invoke the programs in the properties of their icons and enter them as text in the "run as another user" option?

---

### Post by Qrk on 2006-03-03
You can use the command

```
gksudo nautilus
```

and then navigate to your user's desktop and delete them.

---

### Post by uber_drizunk on 2006-03-03
if it's only the icons that is owned by root you can always take ownership of the icon files.

in a terminal type

sudo chown username: /path to icon files

---

