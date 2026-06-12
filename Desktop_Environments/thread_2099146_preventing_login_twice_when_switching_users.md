---
title: "preventing login twice when switching users"
date: 2012-12-28
forum: Desktop Environments
---

### Post by dulx on 2012-12-28
Hi all,

Problem:
One user locked the screen or sent the machine to standby mode and another user wants to login. You'll see xscreensaver, which will start lightdb/gdm if you click "new session" where you can choose the desired user and login with your password. Next you'll get the xscreensaver login again, because your screen is locked and you have to authenticate yourself again. (Another issue of xscreensaver: You can't switch to the "new login" button with your keyboard (at least I didn't find any working key combination)).


I edited the script /usr/bin/xflock4 to call gdmflexiserver and deactivated xscreensaver, but the session will not get locked in this configuration. Yes, you'll get a login prompt when you follow the standard procedure, but if you switch the graphical consoles via function key, you jump into an unlocked session of another user.

Is there a way to get this solved?

Thank you.
Best regards,
dulx

---

