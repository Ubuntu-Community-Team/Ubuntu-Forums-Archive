---
title: "nothing come up after login when installed kde"
date: 2005-10-20
forum: Desktop Environments
---

### Post by jerryhao on 2005-10-20
i upgraded from ubuntu 5.10 to kubuntu, and use dkpg-reconfigure kdm to change login type, then when i reboot and login the screen stopped, and nothing come up, the same situation when i switch it to gdm login, and now only recovery mode works ok. what is the problem?

---

### Post by metoo on 2005-10-21
Good question, can you still get online, e. g. via a router?

Then boot into recovery mode and do the usual:
apt-get update
apt-get upgrade

In any case (even off-line) you can as well try:
apt-get install --reinstall kdm
or
apt-get install --reinstall kubuntu-desktop
to give it a second try.

You may have to add 'sudo ' before the 'apt-get' commands, though.
May be the apt-get messages give you some hints.

---

