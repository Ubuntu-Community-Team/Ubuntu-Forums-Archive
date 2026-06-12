---
title: "X restarting after login??"
date: 2008-01-21
forum: Desktop Environments
---

### Post by debillin on 2008-01-21
Everytime I log into my computer, the screen goes blank and it looks like X is restarting, bringing me to the login window yet again.  It is an endless cycle.

I checked out the X log and the syslog and nothing jumped out at me.

Any ideas??  Thanks!

---

### Post by debillin on 2008-01-21
using the default gnome by the way

---

### Post by apocralypse on 2008-01-28
Me too!!

Would be happy to post logs etc if someone can point me in the right direction.

Sometimes it only restarts if I load certain apps (archive manager, wine, others) :S

Sometimes it just restarts straight away.

Sometimes it goes to a console for a minute then I get a gdm login.

Sometimes it goes to login again straight away.

Help!

The last thing I did was install wine and install flash (studio) with it. This system (Gutsy) has worked well for ages before and has just started doing this.

---

### Post by apocralypse on 2008-01-28
FIXED - for me

I cant find the post that helped me again...

This was an opengl problem cuased by xserver updates... updating nvidia driver fixed it.

---

