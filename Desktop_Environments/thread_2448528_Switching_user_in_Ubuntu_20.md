---
title: "Switching user in Ubuntu 20"
date: 2020-08-09
forum: Desktop Environments
---

### Post by hakelm on 2020-08-09
I normally have two users running root and myself. In Ubuntu 16 and other Linuxes you normally use ctrl-alt-f7 and ctrl-alt-f8 etc. to immediately switch between users but this doesn't  seem to apply to Ubuntu 20.What is in Ubuntu 20 the proper key sequence to switch user?
H

---

### Post by ajgreeny on 2020-08-09
If you go to the logout system in Ubuntu 20.04 you may get the option of Switch User.

If you do not see that in Ubuntu there must be an option at the login screen of GDM (I think that is the Display Manager used) to choose another user.
What do you see if you use Ctrl+Alt+(F1-F6)?  
In my Xubuntu 20.04 that moves me to the tty command lines from tty1 to tty6, and Ctrl+Alt+F7 takes me back to the Xfce4 GUI.

---

### Post by hakelm on 2020-08-09
The problem is that this seems to change haphazardly. Right now when I'm writing this it is ctrl-alt-f2, ctrl-alt-f3. Definitely not the traditional ctrl-alt-f7, ctrl-alt-f8.

---

### Post by ajgreeny on 2020-08-09
You mention two users running as root in your first post here.  What exactly do you mean  by that as we do not support running as root in Ubuntu; the system uses sudo instead of logging in as root.  Logging as root to a GUI session is particularly insecure and not something we discuss in any detail in the forum.

Give us more detail of what exactly you want to do, and why you think that to login as root is necessary, and we may be able to help you further.

---

### Post by CatKiller on 2020-08-09
> **hakelm said:**
> Definitely not the traditional ctrl-alt-f7, ctrl-alt-f8.

Those aren't traditional Ubuntu VTs. 7 used to be used for the graphical session, and 8 used to be used for boot messages. 1-6 were available. Relatively recently the login window got moved to 1.

Also, don't log in as root.

---

### Post by hakelm on 2020-08-10
In Ubuntu 16 you switched to the x-session of the user that logged on first with ctrl-alt-f6, the second with ctrl-alt-f8 etc. If you tried to reach a nonexistent x-session you where presented a cli login.
In Ubuntu 20 you reach the first user with  ctrl-alt-f2, the second with ctrl-alt-f3 etc. A new convenient feature is that ctrl-alt-f1 directly presents you with a graphical login screen for switching user.
H

---

