---
title: "Shockwave Player"
date: 2006-01-09
forum: General Help
---

### Post by ubuntuubuntu on 2006-01-09
How can I install Shockwave Player? I already have the plugin Shockwave Flash. When I visit some pages, its said that there is a missing plugin, and when I click on "click here to download plugin", the page 
[http://sdc.shockwave.com/shockwave/download/download.cgi?](http://sdc.shockwave.com/shockwave/download/download.cgi?)
is open, and it says the following:
" We are unable to locate a Web player that matches your platform and browser."

---

### Post by kwaanens on 2006-01-09
Unfortunately there is no shockwave player for Linux. Macromedia doesn't seem to care.
And I guess their choice will make Shockwave obsolete.

- Ketil

---

### Post by Neo- on 2006-01-16
[QUOTE=ubuntuubuntu]How can I install Shockwave Player? I already have the plugin Shockwave Flash. When I visit some pages, its said that there is a missing plugin, and when I click on "click here to download plugin", the page 
[http://sdc.shockwave.com/shockwave/download/download.cgi?](http://sdc.shockwave.com/shockwave/download/download.cgi?)
is open, and it says the following:
" We are unable to locate a Web player that matches your platform and browser."[/QUOTE]
You can install shockwave player with Crossover or you can just use wine..
Wine guide:
Install firefox (windows version) with wine and with it then shockwave..
Good Luck

---

### Post by rjay3 on 2006-01-17
I have a similar query except my has to do with a flash player which I downloaded. The files that opened up are:
tar:/home/robertoj/install_flash_player_7_linux.tar.gz/install_flash_player_7_linux/flashplayer-installer
tar:/home/robertoj/install_flash_player_7_linux.tar.gz/install_flash_player_7_linux/flashplayer.xpt
tar:/home/robertoj/install_flash_player_7_linux.tar.gz/install_flash_player_7_linux/libflashplayer.so
tar:/home/robertoj/install_flash_player_7_linux.tar.gz/install_flash_player_7_linux/Readme.txt
I tried to follow the installation instructions using the Terminal but get this:
robertoj@rjs3rd:~$ cd '/home/robertoj/install_flash_player_7_linux.tar.gz/install_flash_player_7_linux'
bash: cd: /home/robertoj/install_flash_player_7_linux.tar.gz/install_flash_player_7_linux: Not a directory
robertoj@rjs3rd:~$
Can someone please help? Oh, this is from going to the KDE Eye Candy and a window pops up with "Missing Plugin-Konqueror" No plugin found for Shockwave Flash Media|Do you want to download from [www.macromedia.com?](www.macromedia.com?)
Thanks

---

### Post by Jimmy_r on 2006-02-01
If you do like this:
cd /home/robertoj/
tar -xzf install_flash_player_7_linux.tar.gz
cd install_flash_player_7_linux
./flashplayer-installer

---

