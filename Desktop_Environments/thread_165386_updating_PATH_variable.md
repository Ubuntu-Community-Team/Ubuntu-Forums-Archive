---
title: "updating PATH variable"
date: 2006-04-24
forum: Desktop Environments
---

### Post by binilbenjamin on 2006-04-24
i recently installed java sdk 1.5 in /opt...how do i update PATH variable with this path(which file to update??)

---

### Post by jazzmuzik on 2006-04-24
For a user directory you could edit .bashrc :

export PATH=/path/to/javasdk/bin:"${PATH}"

I'm not sure how to do it globally.

---

### Post by schilcha on 2006-04-24
[QUOTE=jazzmuzik]For a user directory you could edit .bashrc :

export PATH=/path/to/javasdk/bin:"${PATH}"
[/QUOTE]
You can also try to put the same in the file .gnomerc in your home-directory (don't hesitate to create it, if it doesn't exist). .gnomerc is parsed during startup of gnome (after login).

Good luck!

---

