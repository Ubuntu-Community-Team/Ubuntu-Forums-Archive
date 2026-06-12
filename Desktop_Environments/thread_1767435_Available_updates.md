---
title: "Available updates"
date: 2011-05-25
forum: Desktop Environments
---

### Post by lazloman on 2011-05-25
How do I use apt-get or aptitude to tell me what updated packages are available for my system? I'm moving over from Gentoo where I had a cron job that would run a command whose output was a list of available updates. I had this and other system related info emailed to me. I'd like to duplicate that under Ubuntu, but I can't find a way get the available updates.
Thx

---

### Post by MBybee on 2011-05-25
> **lazloman said:**
> How do I use apt-get or aptitude to tell me what updated packages are available for my system? I'm moving over from Gentoo where I had a cron job that would run a command whose output was a list of available updates. I had this and other system related info emailed to me. I'd like to duplicate that under Ubuntu, but I can't find a way get the available updates.
Thx

Like this? The -u -s means simulate, don't actually run the update and show the list.
sudo apt-get update
sudo apt-get -u -s upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  glib-networking rdesktop
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Inst glib-networking [2.28.5-0ubuntu1] (2.28.6.1-0ubuntu1 Ubuntu:11.04/natty-updates [amd64])
Inst rdesktop [1.6.0-3ubuntu4] (1.6.0-3ubuntu4.1 Ubuntu:11.04/natty-updates [amd64])
Conf glib-networking (2.28.6.1-0ubuntu1 Ubuntu:11.04/natty-updates [amd64])
Conf rdesktop (1.6.0-3ubuntu4.1 Ubuntu:11.04/natty-updates [amd64])

---

### Post by lazloman on 2011-05-25
Thanks. It was the -s switch I was missing. I tried -u, but clearly, that wasn't enough.

---

