---
title: "Compiz screenlets"
date: 2008-01-27
forum: Desktop Environments
---

### Post by stubblepoo on 2008-01-27
when i try to install as shown on another thread i get this problem:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
kiran@kiran-laptop:~$ sudo apt-get install screenlets
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
kiran@kiran-laptop:~$ mkdir ~/.config/Screenlets
mkdir: cannot create directory `/home/kiran/.config/Screenlets': File exists
kiran@kiran-laptop:~$ mkdir ~/.config/autostart

what does this mean and what should i do?

---

### Post by jackocleebrown on 2008-01-27
Hello!

You can only run one program that installs updates or packages at one time (to prevent you completely pol-axing your system) have you got update manager or synaptic package manager open? try shutting these programs and running the command again.

Jack,

---

