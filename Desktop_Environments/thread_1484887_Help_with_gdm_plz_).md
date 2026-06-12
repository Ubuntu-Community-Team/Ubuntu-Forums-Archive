---
title: "Help with gdm plz :)"
date: 2010-05-16
forum: Desktop Environments
---

### Post by Mr_VeRiTy on 2010-05-16
Hi, I'm trying to downgrade gdm to version 2.20 in order be able to change gdm themes again, but following the instructions;

(1)sudo /ect/init.d/gdm stop
(2)sudo apt-get install gdm-2.20
(3)cd /ect/gdm
sudo sed  's|x11r6/||' gdm.conf >/tmp/gdm.conf
sudo mv /tmp/gdm.conf .
(5)sudo gdm

The output from the first command was "sudo: /ect/init.d/gdm: command not found"

How can I downgrade, also is it because im running lucid, not karmic koala?

---

### Post by Mr_VeRiTy on 2010-05-16
*bump*

---

### Post by byStanderone on 2010-05-16
...perhaps you followed the same steps as posted in this thread,but do review your syntax, there might be some typo:
[http://ubuntuforums.org/showthread.php?t=1323087](http://ubuntuforums.org/showthread.php?t=1323087)

---

### Post by parn on 2010-05-16
(1)sudo /ect/init.d/gdm stop

think it should be /_etc_/init.d/gdm stop

That is why I alway use the TAB key XD

---

### Post by Mr_VeRiTy on 2010-05-16
Yes I think it was that thanks :)

---

