---
title: "ubuntu on dell"
date: 2009-10-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rizwanhudda on 2009-10-20
I m planning to install ubuntu on my dell inspiron 1545 laptop. Please give me a list of to-dos after installing OS for installing the drivers. The specs of my laptop are:

Code:

processor - Intel core 2 duo cpu T6400 @ 2.00 Ghz
memory -    2 Gb x 2 - DDR2 SD RAM
storage - 320 Gb seagate SATA hard disk.
network - Intel wifi 5100 AGN.
Audio device - IDT high definition audio codec.
Display adapter - ATI mobility Raedon HD 4330.
Mouse pointing device - dell touchpad [ Alps electric ]

My laptop currently has Windows vista home basic, I have used ubuntu in past on my desktop. But,it was like 2 years back. Now, i want to make a partial switch to ubuntu. I intend to use ubuntu as my primary OS after re-install so,give me the instructions to install drivers for my laptop. And, basic softwares for everyday usage.

I intend to use my laptop for playing videos/audio,Creating presentations/reports,browsing net[i use tata indicom photon plus],reading e-books,Writing code in c/c++/java/perl/python/pike,playing games,maintaining contacts,using chat clients[Gtalk],...etc..etc..

Suggest me which version should i install..if there's any special cd for ubuntu..please give me a link..
HELP!HELP!
thanks in advance....

---

### Post by Matt__ on 2009-10-20
Just download an iso to burn to cd from here...9.04
[http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)

everything will work 'out of the box'
you can install gfx drivers from the ATI site, but unless you intend playing 3d games you may as well stick with built in drivers.(I've never got my ATI drivers to work...just crashed ubuntu :P)

run update in the terminal (applications/accessories)```
sudo apt-get update
```then install tweak
```
sudo apt-get install ubuntu-tweak
```install ubuntu restricted extras (for audio/video codecs) and anything else that takes your fancy in the two large lists in ubuntu-tweak (or add/remove programs OR synaptic package manager)
install mplayer/xine/gxine

for java```
sudo apt-get install sun-java6-jre sun-java6-plugin

sudo apt-get install sun-java6-jdk
```install python from add/remove

perl & pike & c++ from synaptic package manager

pidgin multi im client already installed, emesne or aMSN available in synaptic or add/remove

skype from within tweak

update firefox ```
sudo apt-get install firefox-3.5
```openoffice presentation/word/spreadsheet already installed as is gimp image editor

add/remove for DIA diagram editor (uml/iconix)

inkscape is nice for vector gfx (add/remove or synaptic)

and scribus for publications

finally add all the extra repositories using ubuntu-tweak then```
 sudo apt-get update
``` and browse for LOTs of games using synaptic package manger.

I think that covers everything!

ps. synaptic is by far the best way to install most stuff as it auto resolves package dependencies and conflicts.
pps. use ubuntu-tweak applications/package cleaner to remove cached files/clean config/kernel AFTER you've rebooted and everything is working fine.

---

### Post by rizwanhudda on 2009-10-21
Thanks Matt__.
I am ready to install ubuntu now..

---

