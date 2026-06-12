---
title: "Cannot type lowercase 'L' in gnome-terminal"
date: 2011-02-04
forum: Desktop Environments
---

### Post by tzjin anthony ks on 2011-02-04
Hi, All.

A few minutes ago, without any apparent reason, my gnome-terminal started refusing acceptance of lowercase 'L'. When I hit the 'L' key, the menu toggles between visible and hidden. Note, this is lower case 'L', not uppercase.

Does anyone know of any probable causes, and likely fixes?

Thanks.

Tzjin.

---

### Post by Forlong on 2011-02-04
Sounds like you accidentally set a keyboard shortcut. Try this command:
```
gconftool -s -t str /apps/gnome-terminal/keybindings/toggle_menubar disabled
```

---

