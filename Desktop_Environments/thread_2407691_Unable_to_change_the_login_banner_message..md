---
title: "Unable to change the login banner message."
date: 2018-12-06
forum: Desktop Environments
---

### Post by ssatyal on 2018-12-06
I am not being able to change the login banner message. 

Error Message: unable compile /etc/dconf/db/gdm.d: warning: Failed to read keyfile '/etc/dconf/db/gdm.d/01-banner-message.save.2': Key file contains line “org/gnome/login-screen]” which is not a key-value pair, group, or comment

---

### Post by again? on 2018-12-07
> **ssatyal said:**
> I am not being able to change the login banner message. 

Error Message: unable compile /etc/dconf/db/gdm.d: warning: Failed to read keyfile '/etc/dconf/db/gdm.d/01-banner-message.save.2': Key file contains line “org/gnome/login-screen]” which is not a key-value pair, group, or comment

If you copy and pasted the error message correctly it's telling you **org/gnome/login-screen]**
should be **[COLOR="#FF0000"][[/COLOR]org/gnome/login-screen] ** in /etc/dconf/db/gdm.d/01-banner-message.save.2
That is you missed the preceding square bracket "[".

---

### Post by coffeecat on 2018-12-07
Posts moved to own thread, and title amended from original to be more accurately descriptive. 

@ssatyal, please start your own threads, rather than resuscitating or hijacking old threads.

---

### Post by ssatyal on 2018-12-12
@coffeecat  Noted !! Thanks.

---

