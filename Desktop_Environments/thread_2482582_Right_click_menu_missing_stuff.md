---
title: "Right click menu missing stuff"
date: 2023-01-04
forum: Desktop Environments
---

### Post by jax200 on 2023-01-04
Hello
I am using Ubuntu 22.04 in a Virtualbox machine with Windows 10 host.
Unlike earlier distros, when I right-click on the desktop the menu is missing some items, especially 'OpenTerminal' and 'New Folder'.
Currently it just lists 'Change Background', 'Display Settings', and 'Settings'.
The mouse settings doesn't help, nor do the 'Tweaks' and 'Extensions' apps.
How to fix this?

Many thx,  Jack

---

### Post by ActionParsnip on 2023-01-06
What desktop environment please?

---

### Post by tea for one on 2023-01-06
Have a look at this extension [https://gitlab.com/rastersoft/desktop-icons-ng](https://gitlab.com/rastersoft/desktop-icons-ng)
Open a terminal and enter:-
```
sudo apt install gnome-shell-extension-manager
```
Close terminal if successfully installed.
Click Show Applications > Extension Manager > Desktop Icons NG (DING) > Enable extension > Click gear wheel (settings)
Play with it and see if it is suitable?

---

### Post by jax200 on 2023-01-06
Yes, I had installed the 'Extensions' app but didn't see a setting.
But I looked at it again and indeed now all good.
thanks !

---

