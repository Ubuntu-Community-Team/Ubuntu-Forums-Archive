---
title: "GUI doesn't start"
date: 2007-06-17
forum: Desktop Environments
---

### Post by Ice_cone on 2007-06-17
I just installed Ubuntu 7.04 on my ibm notebook (PM 1.3GHz, 256MB ram)
since it doesn't have a cd-rom, i install it using this method: [http://ubuntuforums.org/showthread.php?t=427793](http://ubuntuforums.org/showthread.php?t=427793)
However after installation, it doesn't load the GUI.  (not the server version)
I typed
sudo /etc/init.d/gdm start
it asks my pwd, that nth happened
i went to see /etc/init.d and didn't see a file named gdm
sudo apt-get install xserver-xorg <== also nth happened after this.
What's wrong with it?
thanks

---

### Post by scrooge_74 on 2007-06-24
since you are low on RAM try sudo apt-get install xubuntu-desktop from a terminal

see if you get a desktop after

did you do also sudo dpkg-reconfigure xserver-xorg

---

