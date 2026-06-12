---
title: "Problem saving session"
date: 2005-12-20
forum: Desktop Environments
---

### Post by rich257 on 2005-12-20
When I save a session in Gnome and then logout and log back in again the splash screen is displayed for a long time before the desktop appears.

It seems that there are two copies of metacity running (at least for a while).

If I start with no session (use default or delete the file ~/.gnome2/session and login) then start Gaim and Skype then do Log Out and click Save Session, I get a message saying that the session has been saved.  I think logout without saving the session and log back in again.

This then takes ages.  Selecting System -> Preferences -> Sessions then shows that the current session has two copies of metacity, one with the trash can icon.  If I look at the System Monitor shortly after the desktop appears I usually have three copies of gaim, and later two of them exit.

All very odd.  Can anyone suggest a solution?  This is 5.10 and has been updated from 4.10 to 5.04 to 5.10.

---

### Post by aysiu on 2005-12-21
Maybe System > Preferences > Sessions and kill one of the Metacity apps running, and then save?

---

### Post by rich257 on 2005-12-21
Yes, I have tried removing the surplus metacity and doing apply.  On log out the session is saved, whether I request it or not, and then on logout and bak in again the same thing happens: two copies of metacity and a long login time.

---

### Post by aysiu on 2005-12-21
This may seem an extreme workaround, but if you create a new user, does that new user experience the same problem?

---

### Post by rich257 on 2005-12-21
I have just tried creating a new user and logging in, and yes, once the session is saved and you login again the same thing happens with a long login time, etc.  Interestingly the new user gets a volume control on the panel that I don't think I have had since 5.04

---

