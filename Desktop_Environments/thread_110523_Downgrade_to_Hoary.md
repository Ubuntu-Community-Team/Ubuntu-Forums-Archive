---
title: "Downgrade to Hoary"
date: 2005-12-31
forum: Desktop Environments
---

### Post by mayankgarg1 on 2005-12-31
I have upgraded my PC from 5.05 to 5.10b but after that getting various problems like running in application ie synaptic, disks-admin, users-admin.
please guide me how i can revert back to 5.04 (hoary) as it was working quite good

---

### Post by drfalkor on 2005-12-31
try do add a hoary source.list, and then:
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get upgrade

dunno if it will work, maybe you'll break your system by doing that :???:

---

### Post by mayankgarg1 on 2005-12-31
thanks for your guidence
is there any other way to solve the problem of not running of application.

---

### Post by xyz on 2006-06-20
There-s some talk about it here/
[http://ubuntuforums.org/showthread.php?t=77370&highlight=downgrade+hoary](http://ubuntuforums.org/showthread.php?t=77370&highlight=downgrade+hoary)

---

