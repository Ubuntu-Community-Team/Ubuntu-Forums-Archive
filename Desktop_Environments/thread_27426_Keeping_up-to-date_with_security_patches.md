---
title: "Keeping up-to-date with security patches"
date: 2005-04-16
forum: Desktop Environments
---

### Post by agenkin on 2005-04-16
Is there an official hook for keeping the system patched out of a cron script?  I can put together the usual "apt-get update; apt-get upgrade" stanza, but I am thinking that perhaps there is a 'proper' Ubuntu/Debian way of doing it.

---

### Post by Leif on 2005-04-16
I don't think there is an official method. The closest thing to an official one would be the unofficial guide : [http://ubuntuguide.org/4.10/index.html#autoupdate](http://ubuntuguide.org/4.10/index.html#autoupdate)

---

### Post by ubuntu_demon on 2005-04-16
[QUOTE=Leif]I don't think there is an official method. The closest thing to an official one would be the unofficial guide : [http://ubuntuguide.org/4.10/index.html#autoupdate](http://ubuntuguide.org/4.10/index.html#autoupdate)[/QUOTE]
 I don't like that method because I want auto-update to don't do anything if
1) it needs to install extra packages
2) packages need to be configured

The cronjob I created only does trivial upgrades (not involving user-interaction) and doesn't install a package if additional packages are needed.


$sudo pico /etc/cron.daily/customupdate

```

#! /bin/sh
apt-get update
apt-get upgrade --trivial-only
apt-get autoclean

```

Just place it in /etc/cron.daily and do 

$ sudo chmod +x scriptname

You'll get mail automatically of its output. I just check it once in a while using 'mutt". I also do sudo apt-get update && sudo apt-get upgrade once in a while to see if I missed anything.

---

### Post by az on 2005-04-16
Hoary has the update-manager as part of the desktop...

---

