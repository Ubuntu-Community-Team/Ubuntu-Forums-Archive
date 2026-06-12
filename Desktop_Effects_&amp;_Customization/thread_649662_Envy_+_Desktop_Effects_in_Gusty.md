---
title: "Envy + Desktop Effects in Gusty"
date: 2007-12-25
forum: Desktop Effects &amp; Customization
---

### Post by coreSOLO on 2007-12-25
- After some memory leak issues in 100.xx drivers, I installed latest drivers 169.07 using envy.
- When I check in "restricted driver manager", as obvious, nvidia drivers are displayed as "not installed" but "in use"
- Now when I try to enable "Desktop Effects", it says that restricted drivers are not installed.

Now how do I enable Desktop Effects under these circumstances???

---

### Post by Zorael on 2007-12-25
I'm confused. If you had Envy configure your /etc/X11/xorg.conf file, it should already be using your driver, regardless of what the restricted manager has to say about it. :>

Could you perhaps post said file? Again, /etc/X11/xorg.conf.

---

### Post by Forlong on 2007-12-26
Also post the output of ```
compiz
``` in a terminal.

---

