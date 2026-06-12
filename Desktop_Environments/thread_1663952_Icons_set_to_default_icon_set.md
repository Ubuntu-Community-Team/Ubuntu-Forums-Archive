---
title: "Icons set to default icon set"
date: 2011-01-10
forum: Desktop Environments
---

### Post by group256 on 2011-01-10
Hi everyone,

Yesterday I added a script under home/sam/.gnome2 folder of my ubuntu 10.10 in order to open my folders as root, here is the script:

```

for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
gksudo "gnome-open $uri" &
done

```

Now when I restarted today, I mentioned that all my icons and configuration has gone to default GRAY set. But if I click on any folder and click on open as root, then all my themes and configuration come back.

I was wondering if there is anything I need to know to fix this. Thanks a lot.

---

