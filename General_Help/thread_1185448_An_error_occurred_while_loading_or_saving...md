---
title: "An error occurred while loading or saving.."
date: 2009-06-12
forum: General Help
---

### Post by ade234uk on 2009-06-12
Keep getting this error appear in Ubuntu every so often. Does anyone know how to solve this? Error is below

--------------------------------------
An error occurred while loading or saving configuration information for evolution-alarm-notify. Some of your configuration settings may not work properly.

Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-8GFKPqutfI: Connection refused)

---

### Post by vanadium on 2009-06-25
I recently also have this error. Your post turned up first in a Google search, congrats ! ;)

---

### Post by tomh5 on 2009-06-26
I had this same error along with the same in update-manager which prevented me from logging in. To solve it I logged into a failsafe terminal session from the login screen and then used the command suggested at [http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/.]("http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/")

This is to type the command,
**rm -rf .gnome .gnome2 .gconf .gconfd .metacity**
which removes all your gnome desktop settings so that they are reset to default on the next login.

Hope this helps someone.

Tom

---

