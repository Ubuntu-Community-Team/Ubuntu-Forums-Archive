---
title: "[SOLVED] gnone panel delay on login"
date: 2008-08-23
forum: Desktop Environments
---

### Post by mike2357 on 2008-08-23
Occasionally when I log in, there is a long delay (around two minutes) before my desktop's two gnome panels load.  I don't see any pattern, except that it never seems to happen on the first login after a boot.  When the problem occurs, there is a sliver of a panel, which stays the same for the two-minute period.

Any ideas?

---

### Post by cprofitt on 2008-08-23
> **mike2357 said:**
> Occasionally when I log in, there is a long delay (around two minutes) before my desktop's two gnome panels load.  I don't see any pattern, except that it never seems to happen on the first login after a boot.  When the problem occurs, there is a sliver of a panel, which stays the same for the two-minute period.

Any ideas?

I have noticed the same thing, but I do not have any ideas... but it has not been long enough to bother me yet.

---

### Post by mike2357 on 2008-08-24
Bump.

---

### Post by kerry_s on 2008-08-24
it's a session thing.

1. open preferences> sessions, click on the startup programs tab and disable all of them.

2. log out and back in, open the session manager again, click the current session tab, in the order move all of them to 00(see pic) and apply, in session options click "save the current session".

3. log out and back in, in the session startup, reenable what ever is not already running in current session.

4. log out and in 1 last time.

make sure ~/.metacity/sessions only has 1 session in it, if there's more than 1 delete them all before you do the 1 to 4 steps, it will create 1 session, i also created a default0.ms it's just a file with 0 in it, that just stops the xsession.error log, just to keep things clean.

some times, for some reason, it gets slow again, usually when you mess with the panel, just repeat the steps and it'll be back up to speed.

---

### Post by mike2357 on 2008-08-24
Thanks Kerry.  I never would have figured it out.

---

### Post by kerry_s on 2008-08-24
> **mike2357 said:**
> Thanks Kerry.  I never would have figured it out.

:lolflag: it took me days of looking at the logs and trying to figure out what it was doing.

---

