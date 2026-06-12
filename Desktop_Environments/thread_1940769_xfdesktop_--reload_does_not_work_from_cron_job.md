---
title: "xfdesktop --reload does not work from cron job"
date: 2012-03-14
forum: Desktop Environments
---

### Post by ohnonot on 2012-03-14
i have a little shell script to update my desktop background from the internet.

when i run it manually it works nicely, but when i run it automatically once an hour via gnome-schedule (works on xfce), the last bit, reloading the desktop, does not work.

what to do?

i heard that cron jobs (i think gnome schedule usues cron) are run as root.
i also heard that xfdesktop is tricky with that - but the explanation went 404.
i also found an old article from 2008, telling me to manually edit crontab... haven't tried it
i also found the killall solution, but i don't want to use it because it makes my screen go white for a moment.

i tried various combinations of running the last command or the whole script as sudo -u myusername, but to no avail.

what now?
:confused:
asks a semi-noob-nerd.

---

### Post by LewisTM on 2012-03-14
What about this?
```
su yourname -c "xfdesktop --reload"
```
Works here in a root terminal

Cheers!

---

