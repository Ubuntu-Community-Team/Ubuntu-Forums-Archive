---
title: "[SOLVED] Removing KDE login manager from Ubuntu"
date: 2007-11-12
forum: Desktop Environments
---

### Post by dcroxton on 2007-11-12
I recently did a fresh install of Gutsy, then I installed KDE to experiment with it.  I like it, but the screen invariably freezes if I don't use it for more than a few minutes.

I don't care to solve this problem at the moment; I just want to go back to Gnome.  I can set the session to Gnome when I log in, but I still get the KDE login managers + kdm, and the login screen is subject to the same problem that if I don't login very soon, it will lock up and force me to reboot.  What's the best way to switch back to gdm + Gnome login?  I don't care too much whether this involved removing KDE packages or just setting the system to ignore them.  I'm just afraid to touch anything since I had to do the clean install of Gutsy after 2 + years of using Ubuntu with just regular upgrades; I don't want to screw anything up so I have to do another clean install, as getting all my program back was a real pain.

Thanks,
Derek

---

### Post by kellemes on 2007-11-12
You could reinstall gdm, as far as I know it will ask to become default loginmanager.

---

### Post by aysiu on 2007-11-12
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome) should help.

---

### Post by dcroxton on 2007-11-12
Thanks for the help.  Just re-installing gdm didn't work.  The link to psychocats did.  It removed MySQL and ProFTP for some reason, but I can re-install two programs easily enough.

Sincerely,
Derek

---

