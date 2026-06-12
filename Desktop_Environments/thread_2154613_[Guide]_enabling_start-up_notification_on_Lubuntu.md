---
title: "[Guide] enabling start-up notification on Lubuntu"
date: 2013-06-15
forum: Desktop Environments
---

### Post by k9einzwei on 2013-06-15
1. open LXTerminal
2. sudo add-apt-repository ppa:kubuntu-ppa/backports
3. sudo apt-get update
4. sudo apt-get install kde-window-manager
5. sudo vi /etc/xdg/lxsession/Lubuntu/desktop.conf
6. replace : openbox-lubuntu with kwin
7. save
8. sudo reboot
9. enjoy :D

---

