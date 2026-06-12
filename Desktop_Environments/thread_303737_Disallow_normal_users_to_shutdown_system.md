---
title: "Disallow normal users to shutdown system"
date: 2006-11-20
forum: Desktop Environments
---

### Post by horvatj on 2006-11-20
Hello folks!

Can you tell me how to disallow normal users to shutdown or reboot the system using ubuntu 6.10 with gnome.

***AND***: is it also possible to hide the shutdown and restart buttons from the logoff screen?

Thank you
Johann
:rolleyes:

---

### Post by speedman on 2006-11-20
You can remove the options to shutdown and reboot the system from GDM (graphical login) by editing /etc/gdm/gdm.conf and changing this line:

#SystemMenu=true

... to read:

SystemMenu=false

With regards to the Gnome logout options for shutting down and rebooting the system the presence of a file named after currently logged in user(s) in /var/run/console is what enables these privileges.  In other words, if you remove the file named after the user from that directory they will not be presented with the options to shutdown, or reboot the system when they log out.  A simple script called by cron to delete specific user files in /var/run/console would do the trick.

Hope that helps.


Regards,

SM

---

