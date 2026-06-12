---
title: "Updating issues."
date: 2006-06-12
forum: Desktop Environments
---

### Post by woopud on 2006-06-12
If i try to do the update manager i get the following message:

Cannot install all available updates

Some updates require the removal of further software. Use the function "Smart Upgrade" of the package manager "Synaptic" or run "sudo apt-get dist-upgrade" in a terminal to update your system completely.

So, I open a terminal and type:

woopud@ubuntu:~$ sudo apt-get dist-upgrade
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
woopud@ubuntu:~$

and get this messgae, what's up with that ?
Bert

---

### Post by ayoli on 2006-06-12
The apget error comes because you have to close all update manager and/or synaptic instances before run apt-get.

---

