---
title: "XFCE disable saving session"
date: 2011-08-01
forum: Desktop Environments
---

### Post by decoherence on 2011-08-01
Hi,

I'm running Xubuntu and whenever I log in XFCE starts all the of programs I had running when I logged out, causing me to tap my foot impatiently and grumble while I wait for a usable desktop.

I've gone in to Settings -> Session and Startup and I see that "automatically save session on logout" is unchecked. Is there something else I'm missing that I need to do to get XFCE to stop this annoying (to me) behavior?

thanks,

---

### Post by Toz on 2011-08-01
You can reset the xfce sessions startup list by deleting the ~/.cache/sessions directory. You should probably do this when you are not logged in, though. It will be recreated on your next graphical login.

---

