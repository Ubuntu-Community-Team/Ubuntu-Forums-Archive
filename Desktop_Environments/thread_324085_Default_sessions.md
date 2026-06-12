---
title: "Default sessions"
date: 2006-12-23
forum: Desktop Environments
---

### Post by Obor on 2006-12-23
I got gnome and kde-core on my pc. **What I would like to do is to have Gnome as default session for one user and kde-core as a default session for another user.**

Is there a way to achieve this without going to sessions at startup all the time? I think I read about it some time ago on forums but can't find it anymore.

At the moment I have gnome as default and when the 2nd user logs in he has to choose kde as a session, which is bit troublesome because if he forgets to do it he has to logout again etc.

---

### Post by fdoving on 2006-12-23
Yes, you can do this.

use each users ~/.xsession file and select 'default session' at the login managers session menu.

for KDE it should contain:
```

exec startkde

```

for GNOME it should be:
```

exec gnome-session

```


Hope this helps

- Frode

---

### Post by Obor on 2006-12-23
Thanks for that.

---

