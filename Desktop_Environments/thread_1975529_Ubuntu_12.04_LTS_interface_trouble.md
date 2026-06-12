---
title: "Ubuntu 12.04 LTS interface trouble"
date: 2012-05-07
forum: Desktop Environments
---

### Post by Palmer Eldritch on 2012-05-07
Hello,
 
I'm trying to finish setting up a desktop running Ubuntu 12.04 LTS 32bit.
 
Everything is about OK, but after a mishandling, I no longer have the choice to stop or restart the system but only to stop it under Unity interface. (With the session control menu, I can lock the screen, log out, hibernate or shut down the machine but no more restart the system…)
 
Does anyone know how to restore normal operation?
 
Thanks!
 
Regards,
Palmer.

---

### Post by mc4man on 2012-05-07
By default restart is available from the shutdown option in the 'session control menu', do you not have that? - screen

---

### Post by Palmer Eldritch on 2012-05-07
> **mc4man said:**
> By default restart is available from the shutdown option in the 'session control menu', do you not have that? - screen
Thank you for your answer!
 
Unfortunately no!

---

### Post by Palmer Eldritch on 2012-05-07
Oops ... Meanwhile it seems I've found the solution to my concern.
 
This was apparently because I used gconf-editor which is deprecated in Ubuntu 12.04, when I should instead use dconf-editor.
 
Thank you all anyway!
 
Regards,
Palmer.

---

