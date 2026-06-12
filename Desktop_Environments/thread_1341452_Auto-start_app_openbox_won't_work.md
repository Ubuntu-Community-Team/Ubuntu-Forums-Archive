---
title: "Auto-start app openbox won't work"
date: 2009-11-29
forum: Desktop Environments
---

### Post by pantone186 on 2009-11-29
Hello all,

I'm unable to auto-start an app (sjog) in a ubuntu 9.04 installation using openbox wm.

I have tried in autorstart.sh:

sjog &

exec sjog &

(sleep 2-10 && sjog) &

also tried chown and chmod on the app too, but without success.

Any help would be appreciated

---

### Post by Locutus_of_Borg on 2009-11-29
(sleep 2 && sjog)&

in .config/openbox/autostart.sh

chmod +x .config/openbox/autostart.sh

ensure you are using /usr/bin/openbox-session and not simply /usr/bin/openbox to start your session from the login manager

---

