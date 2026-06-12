---
title: "gnome-panel removed, autologin tries to use it, black hang screen"
date: 2012-01-13
forum: Desktop Environments
---

### Post by mbogevik on 2012-01-13
Hi,

I have tried gnome-panel (sudo apt-get install gnome-panel) in Ubuntu 11.10 and set it to autologin on gnome-shell with this command : sudo /usr/lib/lightdm/lightdm-set-defaults -s gnome-shell

I then decided to revert to Unity.  I removed gnome-panel using "sudo apt-get remove gnome-panel" and "sudo /usr/lib/lightdm/lightdm-set-defaults -s ubuntu" to go back to Unity autologin.

My problem now may be that the last command did not work, reboot ends in a black screen with text login in small chars and computer freeze, but not entirely, only power button works, switching off.

I have gone into debug terminal and switched off autologin and also installed gnome-panel again without any other result.

I am now locked out of my computer so any idea to get around this problem would really be appreciated ?

---

### Post by mbogevik on 2012-01-13
By combining tip on issues like this I finally managed to solve this.  Even that computer seems to hang I managed to get terminal working with Alt + Ctrl + F1.  I then logged in with text based command prompt and entered "sudo pkill x".  The normal graphic login screen finally came up.

I finally now can set things up as it should after upgrading from 11.04 to 11.10 :)

---

