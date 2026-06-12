---
title: "LXDE desktop files: Terminal=true does not work"
date: 2018-11-27
forum: Desktop Environments
---

### Post by pvigo on 2018-11-27
Hi,

I try to exec an script in terminal and I found that option **Terminal=true** does not work in a Desktop file.
It's easy to reproduce, you can test it with **galculator.desktop**

What can I do? How to open an issue about that?

---

### Post by again? on 2018-11-28
Testing in Lubuntu I don't see a problem.
What's you're base system.

Tested using this desktop file.
Save as test.desktop and make executable.
```
[Desktop Entry]
Name=test
Icon=info
Exec=notify-send -i info "Its working"
Terminal=true
Type=Application
StartupNotify=true
```

Note that when a command or script ends the terminal will close.

---

