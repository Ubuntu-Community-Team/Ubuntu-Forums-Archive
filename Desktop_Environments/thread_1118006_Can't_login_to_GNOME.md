---
title: "Can't login to GNOME"
date: 2009-04-06
forum: Desktop Environments
---

### Post by zeno23 on 2009-04-06
When I try to login to GNOME from the graphical login, after a delay (about 30 seconds) the screen will briefly switch to console display before restarting the graphical login.

I can login at the console by using CTRL+ALT+F1. I have tried using the "Failsafe GNOME" session and the "Failsafe Terminal" session --- both lead to the same behavior described above. I have tried reconfiguring X, GNOME, and GDM. No luck so far.

UPDATE: I created a new user account, and I'm able to login using the new account. How can I tell what's failing in the main account?

---

### Post by ajgreeny on 2009-04-06
Double check your username and password for the first non-working user.  You will see both usernames as folders in /home.  You can also change the password using recovery mode from the grub menu, should that be needed.  Don't forget linux is case sensitive, just in case you were not aware, so Tom, tom, tOm, etc etc are all different to your system.  Apologies if you already knew that, but some people who remember ms-dos do not know.

---

### Post by ronocdh on 2009-04-06
> **ajgreeny said:**
> Double check your username and password for the first non-working user.  You will see both usernames as folders in /home.  You can also change the password using recovery mode from the grub menu, should that be needed.  Don't forget linux is case sensitive, just in case you were not aware, so Tom, tom, tOm, etc etc are all different to your system.  Apologies if you already knew that, but some people who remember ms-dos do not know.
Sounds to me like OP can log in, but there is a graphical display problem. I'm not sure about how to reset the GNOME options (I spend much more time tinkering with X), but there's got to be a way to purge GNOME settings and have the system reconfigure from defaults. The fact that the newly created account works means the old user account has borked settings somehow.

If you can log in via a terminal, and have an internet connection, you might want to consider purging GNOME and related packages, then reinstalling them.

---

### Post by zeno23 on 2009-04-06
Thanks for the reply. There doesn't seem to be a problem with the username and password that I'm using, since I can log in at the console. It would appear that there's something specific to the user account in the GNOME startup that's failing and does not get bypassed in the Failsafe session.

---

### Post by ajgreeny on 2009-04-06
OK, so try renaming the old ~/.gconf folder as backup and try to login again.  It may be that causing the problem.  Perhaps also look at ~/.config/autostart, just in case something in there is conflicting with the startup of gnome.

---

