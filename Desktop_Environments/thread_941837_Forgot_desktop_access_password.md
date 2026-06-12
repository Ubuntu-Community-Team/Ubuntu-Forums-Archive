---
title: "Forgot desktop access password"
date: 2008-10-08
forum: Desktop Environments
---

### Post by dimarec on 2008-10-08
I forgot my password and username. how can I log back into Ubuntu?

---

### Post by ajgreeny on 2008-10-08
Boot into recovery mode.  You can then do anything you like such as change password and username if you want to, but you can find your username by looking to see what is in the /home folder with the command ```
cd /home && ls
```The output of that will be your username.  You can now change the forgotten password to something by using ```
passwd username
```You will be asked to enter the new password twice, but I think nothing will show on screen, but don't worry it will be there.  Now issue the command ```
reboot
``` Just make sure you remember them this time.

---

