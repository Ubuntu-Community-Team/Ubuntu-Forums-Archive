---
title: "Runit Issues"
date: 2006-09-14
forum: Desktop Environments
---

### Post by crexor on 2006-09-14
So I decided to give parallel service loading a stab and installed cinit, which worked fine, then went back to init, then read about runit and how it was a lot better, performance wise, than cinit/init/etc. Well, I installed it, and I could never get run level 2 configured, I switched to the terminal it loaded on tty/4, and played around with it some more, to no avail, so i uninstalled it, well, now it is completely broken. No terminal loaded on any tty, nada, now im thinking the only recovery option is to boot from a live cd and try to fix it there, but im unsure of where to go after that, runit still tries to load, and i was wondering how i tell it to go back to init.

---

### Post by crexor on 2006-09-14
rebooted using init=/sbin/init.sysv which the original /sbin/init after installation of runit. hope this helps all who face this samae issue.

---

