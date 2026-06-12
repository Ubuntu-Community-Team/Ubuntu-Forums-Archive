---
title: "brightness control problem with ubuntu 10.10"
date: 2011-05-25
forum: Desktop Environments
---

### Post by pittump on 2011-05-25
hi i am using Samsung N150 and ubuntu 10.10 is installed in it.
there is problem with brightness control i.e i can not control my brightness by up& down keys. i search many forums for solution and made settings such as:



i Add the repository to the sources list and enable it
sudo add-apt-repository ppa:voria/ppa
Perform complete system update
sudo apt-get update && sudo apt-get upgrade
it may take long time depending the internet connection
than I installed packages ‘samsung-backlight’ and ‘easy-slow-down-manager’
sudo apt-get install samsung-backlight easy-slow-down-manager

also i made changes in brightness setting in during the boot i.e set to user control instead of automatic.
but after doing all these stuff still my laptop brightness not control by fn + up/down keys.
pl help me as soon as possible
mail me solution @ [email]pittump@gmail.com[/email]

---

### Post by Copper Bezel on 2011-05-25
From what I can tell, that PPA isn't current. If you add the Brightness Control applet to the Gnome Panel, does it work?

---

