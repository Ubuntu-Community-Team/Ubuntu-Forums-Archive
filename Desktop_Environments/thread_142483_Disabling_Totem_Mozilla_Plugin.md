---
title: "Disabling Totem Mozilla Plugin"
date: 2006-03-10
forum: Desktop Environments
---

### Post by Steve1961 on 2006-03-10
My totem mozilla plugin launches whenever I stream movies with Firefox, but I prefer the mplayer plugin.  Does anyone know of a way to change the priority of plugins in Fiorefox so that mplayer launches as the default when I click on a video link?  I looked at uninstalling totem but it would remove the desktop in the process.

---

### Post by aysiu on 2006-03-10
```
sudo rm /usr/lib/mozilla-firefox/plugins/totem*
``` should do it.

By the way, it's safe to remove the *ubuntu-desktop* package. It's just a meta-package--it's not a real one.

---

### Post by Steve1961 on 2006-03-10
That did it.  Many thanks.

---

