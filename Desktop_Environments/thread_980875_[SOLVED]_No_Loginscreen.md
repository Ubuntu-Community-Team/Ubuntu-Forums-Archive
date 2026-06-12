---
title: "[SOLVED] No Loginscreen"
date: 2008-11-13
forum: Desktop Environments
---

### Post by Jonathan45 on 2008-11-13
Hi I've just uninstalled KDE4 on my Ubuntu(GNOME) computer and i have by mistake made KDM default.
I just get some black text how i want to login...
Do i have to reinstall ubuntu or GDM or just somehow use a failsafe terminal..
Thanks for taking your time reading this!
(im using hardy heron)

---

### Post by prshah on 2008-11-13
> **Jonathan45 said:**
> Hi I've just uninstalled KDE4 on my Ubuntu(GNOME) computer and i have by mistake made KDM default.
I just get some black text how i want to login...
Do i have to reinstall ubuntu or GDM or just somehow use a failsafe terminal..

At your (broken) login screen, press Ctrl_Alt_F1. This should take you to a text-only virtual terminal. Login with your usual username and password. then give the command ```
sudo /etc/init.d/kdm stop
``` to stop the KDE desktop manager. Follow it with the command ```
sudo /etc/init.d/gdm start
``` When this shows as started ("[OK]"), switch back to the login screen with Ctrl_Alt_F7 (In some cases, it may be F9 or F10). 

If you now have a proper login screen, press F10, and select "Change session", and choose "Gnome". Then continue the login. After you give your password, you will be asked if you want the Gnome session to be the default, or just for this one time. Choose "Make default".

Post back if you run into difficulties starting gdm.

---

### Post by Jonathan45 on 2008-11-13
Yea im gonna try it soon when i got the time.
thanks

---

### Post by Jonathan45 on 2008-11-13
Well...
I tried it and it didn't work.
It couldn't find kdm and it woldn't launch gdm because it wasn't default display manager.:confused:
but thanks anyway.
I hope some1 finds anything.
can i install 8.10 easily on my 8.04 partition?
:popcorn:

---

### Post by prshah on 2008-11-13
> **Jonathan45 said:**
> 
It couldn't find kdm and it woldn't launch gdm because it wasn't default display manager.

I suspected that would be a problem, no matter.. you can set gdm to be your default window manager with the command ```
sudo dpkg-reconfigure gdm
``` You need a reboot for the changes to take effect.

---

### Post by Jonathan45 on 2008-11-13
THANK YOU SO MUCH!!!!!
IT REALLY HELPED THE COMPUTER IS NORMAL AGAIN!
sorry caps.:guitar:

---

