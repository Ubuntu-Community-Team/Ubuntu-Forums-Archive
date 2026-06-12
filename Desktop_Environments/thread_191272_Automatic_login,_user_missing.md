---
title: "Automatic login, user missing?"
date: 2006-06-07
forum: Desktop Environments
---

### Post by nolodude on 2006-06-07
Ok sorry about topic but didn't know how to put it. Situation is this: I installed Dapper. I installed MythTV, which installs mythtv user. I made a password for mythtv user with "sudo passwd mythtv".

Now, when GDM starts up, I can login manually with mythtv user just fine. But in Gnome, if I go to *System -> Administration -> Login window* and to* Security* tab, select *Enable automatic login*, the users-selection box lists only the default username I used when I installed Dapper. I tried inputting *mythtv* by hand but it doesn't stick when I close the dialog box and open it again. I also tried setting automatic login for mythtv by manually editing /etc/gdm/gdm.conf-custom but it just doesn't work :(

There's probably something wrong with the mythtv user account. For some reason, it doesn't appear to be "equal" to my default username, although it should be. 

Any help is appreciated!

---

### Post by marwal on 2006-06-07
Did you add (included) the user in the Users tab (system->admin->login)?

---

### Post by nolodude on 2006-06-07
Tried that now and that had no effect. But I just rebooted my PC and it logged in automatically :D I didn't realize it needed a reboot, I just tried to restart GDM over and over again.

This is solved. Thanks for your help!

---

