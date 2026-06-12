---
title: "gdm gui logon error"
date: 2005-11-12
forum: Desktop Environments
---

### Post by hoover93 on 2005-11-12
i've just upgraded to 5.10 from 5.04 using the sudo apt-get dist-upgrade method.

now, when i boot my system i receive the the following error when the gui login is presented:

"Configuration is not correct.  The configuration file contains an invalid command line for the login dialog, so running the default command.  Please fix your configuration."

when I click OK to clear the error message, i am presented with a generic gnome desktop manager login screen.  i imagine the system should be displaying a gui login box promoting ubuntu.

this generic gnome login box must be the "default command" referred to in the error message.  i tried to look around in /etc/gdm/gdm.conf to find the problem but i was lost in this long configuration file.

a little help please?

---

### Post by Kapre on 2005-11-12
[QUOTE=hoover93]i've just upgraded to 5.10 from 5.04 using the sudo apt-get dist-upgrade method.

now, when i boot my system i receive the the following error when the gui login is presented:

"Configuration is not correct.  The configuration file contains an invalid command line for the login dialog, so running the default command.  Please fix your configuration."

when I click OK to clear the error message, i am presented with a generic gnome desktop manager login screen.  i imagine the system should be displaying a gui login box promoting ubuntu.

this generic gnome login box must be the "default command" referred to in the error message.  i tried to look around in /etc/gdm/gdm.conf to find the problem but i was lost in this long configuration file.

a little help please?[/QUOTE]


I dont know if I understand your problem correctly but if you want to get the GDM to show the default ubuntu GDM (one that is promoting the distro). You can change it in System-----Administration--------Login Screen Setup--------got to the Themed Greeter tab and select the Ubuntu GDM that you want (circle of friends or Ubuntu)

K

---

### Post by hoover93 on 2005-11-12
thanks kapre,

i went through the steps that you outlined, however, i found that the system is already set for the ubuntu graphical greeter.

for whatever reason (i suspect an error in gdm.conf) the system is ignoring or unable to use the ubuntu graphical greeter.

anybody familar enough with gdm.conf to point me in the right direction?

---

### Post by hoover93 on 2005-11-12
i've solved my own problem.  i found another variation of the config file in the /etc/gdm directory:

gdm.conf.dpkg-dist

i copied /etc/gdm/gdm.conf.dpkg-dist to /etc/gdm/gdm.conf

rebooted and all was well.

---

