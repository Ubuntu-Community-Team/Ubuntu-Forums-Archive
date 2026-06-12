---
title: "removing kpanel"
date: 2006-07-26
forum: Desktop Environments
---

### Post by safknw on 2006-07-26
I'm making a new distro based on kubuntu, I don't want kpanel to start automatically on logging. How I can do this. thanks in advance.

---

### Post by Jucato on 2006-07-26
look for /usr/share/autostart/panel.desktop and **move** it somewhere else (you need root privileges). I recommend moving it, just in case you want it back.

Alternatively, you can still have Kicker (the KDE Panel) to start upon logging, but still hidden. If this is the case, you can add this line in the panel.desktop file:

> Hidden=True

Note that since you are modifying /usr/share/autostart, these changes will affect the whole system, including other users.

---

