---
title: "Hardy - Nautilus Script - Open as Root"
date: 2008-04-26
forum: Desktop Environments
---

### Post by maxweld on 2008-04-26
Under earlier versions of Ubuntu I have a script in **"home/me/.gnome2/nautilus-scripts/Open as root"** which allowed me to open files as root, requesting a password, and using gksudo. This no longer works under Hardy.

the script contains:

```
for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
	gksudo "gnome-open $uri" &
done
```

Any ideas what needs to be done to get a similar function under Hardy?

Thanks

---

### Post by Coolit on 2008-04-26
If I need elevated privileges in nautilus I normally just open a terminal and type "sudo nautilus"

You could put that in a script I guess:)

---

### Post by nicedude on 2008-04-26
look for nautilus scripts, I found a package installed it and now I have like 60+ scripts in 7 or 8 categories that work off right click.

---

### Post by Linja on 2008-04-26
Install nautilus-gksu from the repositories. However, this is currently affected by a bug which prevents it from appearing in the context menu. You'll have to copy or link the lib from /usr/lib/nautilus/extensions-1.0 to /usr/lib/nautilus/extensions-2.0 and then run a killall nautilus.

---

### Post by maxweld on 2008-04-26
Thanks all.

I like the suggestion from Coolit as a temporary workaround, but once the nautilus-gksu package is working, I will use it. Thanks

---

