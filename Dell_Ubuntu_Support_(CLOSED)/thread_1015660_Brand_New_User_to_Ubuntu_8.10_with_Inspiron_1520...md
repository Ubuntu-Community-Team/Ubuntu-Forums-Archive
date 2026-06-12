---
title: "Brand New User to Ubuntu 8.10 with Inspiron 1520...experiencing problems...NEED HELP!"
date: 2008-12-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ink59 on 2008-12-19
Dear reader,

Today I just installed Ubuntu 8.10 on my laptop to get more familiar with this OS since we use it at school.

My laptop specs are:
Dell Inspiron 1520
Intel Core 2 Duo T7100 1.8GHz
2.00 GB RAM
NVIDIA GeForce 8600M GT
Dell wireless 1505 mini-n card

Well from the get go my problems are getting my wireless card to work. I have been scouring many forum posts/pages on the net to figure out how to get a driver for the wireless. I came across something called ndiswrapper...

Firstly, is this the right path to follow to use this program or whatever it is...

I am totally new to Ubuntu so any help would be greatly appreciated, and a problem I have is how to even install this 'ndiswrapper' or the appropriate driver. All I know is it's done through the terminal (right???).

SO ya, any help for a complete beginner (LINUX dummy i guess) whose used windows my whole life would be great help!!!

Thanks to all posters in advance!

---

### Post by hexteq on 2008-12-19
(you will need to plug an ethernet cable into your router for this to work)

if you're running the default install, with the menu bar on top, go to System -> Administration -> Hardware Drivers  your wireless driver should show in the list. Click enable and it will download and configure everything you need. if your wireless isn't picking up any routers, you may need to reboot after it completes.

---

### Post by taget on 2008-12-19
also a good soure of info is this page

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by ink59 on 2008-12-19
> **hexteq said:**
> (you will need to plug an ethernet cable into your router for this to work)

if you're running the default install, with the menu bar on top, go to System -> Administration -> Hardware Drivers  your wireless driver should show in the list. Click enable and it will download and configure everything you need. if your wireless isn't picking up any routers, you may need to reboot after it completes.

ok so i have tried hooking up to ethernet and that works (i am writing this post in ubuntu now) however my wireless card doesn't show up. there are some Nvidia drivers to activate however when i press activate the whole window just closes on me abruptly...strange :S

also, there is one driver called 'wl' i am assuming that that is the wireless one, however it was already activated even when the wireless didn't work

---

### Post by ink59 on 2008-12-19
arrghhh i am trying to install my nvidia driver but i get the following error in the terminal:
'ERROR - nvidia installer must be run as root'


what is that supposed to mean?????

---

### Post by punkybouy on 2008-12-21
You could use EnvyNG to install your video driver.  I believe it is in the repositories but I don't remember or run the command you ran before with "sudo" before it and you will be prompted for your user password.  The program should run.

---

### Post by bgblanch on 2008-12-30
> **ink59 said:**
> arrghhh i am trying to install my nvidia driver but i get the following error in the terminal:
'ERROR - nvidia installer must be run as root'


what is that supposed to mean?????


Are you installing from a terminal?  If you are just put sudo in front of what you are running.  It will ask for your password and you're off to the races.

---

### Post by clw3388 on 2008-12-30
dude in this forum [http://ubuntuforums.org/archive/index.php/t-586595.html](http://ubuntuforums.org/archive/index.php/t-586595.html)
has/had the 1505 dell wireless card and go it to work...

---

