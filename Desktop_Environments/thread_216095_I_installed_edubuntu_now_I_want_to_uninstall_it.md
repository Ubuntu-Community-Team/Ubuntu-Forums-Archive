---
title: "I installed edubuntu now I want to uninstall it"
date: 2006-07-14
forum: Desktop Environments
---

### Post by madelman on 2006-07-14
I tried edubuntu, now I want to instalal ubuntu and typing apt-get remove edubuntu and apt-get install ubuntu, nothing happens and still edubuntu keeps popping up, so how do I remove edubuntu?. The options in sessions are:

Last session
Default System Session
GNOME
failsafe GNOME
failsafe terminal

whatever I choose it is edubuntu all the time, how come it still booting wheni remove it?

---

### Post by aysiu on 2006-07-14
This won't solve your problem, but for the future always install with *aptitude*, not *apt-get*.

[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

I'm going to work on some kind of workaround in the meantime that should work but may not 100%, especially if you're using MySQL or PHP.

---

### Post by Gordon Farmer on 2006-07-14
*I tried edubuntu, now I want to instalal ubuntu and typing apt-get remove edubuntu and apt-get install ubuntu, nothing happens and still edubuntu keeps popping up, so how do I remove edubuntu?.*


Logically it seems that is what one would do, 'uninstall', then 'install'.
In you're case I think what you would do is to leave edubuntu installed, and you would 'install ubuntu' on top of edubuntu. Edubuntu would not survive this, and you would be left with ubuntu installed.

But be advised that if you do this, you will loose any files you have created using edubuntu, and you would be using a fresh install of ubuntu.  Everything previous with Edubuntu would be gone.

---

### Post by aysiu on 2006-07-14
Edubuntu is not a desktop environment. It is just a bunch of other packages on top of Gnome.

Okay. Here's the workaround. Copy and paste these commands into the terminal: ```
sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo apt-get remove atomix atomix-data blender denemo dia-common dia-gnome dia-libs edubuntu-artwork edubuntu-artwork-usplash edubuntu-desktop gcompris gcompris-data gcompris-sound-da gcompris-sound-de gcompris-sound-en gcompris-sound-es gcompris-sound-fr gcompris-sound-it gcompris-sound-pt gcompris-sound-ru gcompris-sound-sv gnome-icon-theme-gartoon gpaint gsfonts-x11 kalzium kanagram kbruch kdeedu-data kdelibs-bin kdelibs-data kdelibs4c2a keduca khangman khelpcenter kig kino kmplot kpercentage kstars kstars-data ktouch ktuberling kturtle kverbos kvoctrain kwordquiz libarts1c2a libartsc0 libavahi-qt3-1 libboost-python1.33.1 libcompress-zlib-perl libgcompris-1-0 libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl libkdeedu3 libkdegames1 libmailtools-perl liboggflac3 libopenexr2c2a libpcre3 libqt3-mt libquicktime0 libsamplerate0 libsdl-image1.2 libsdl-mixer1.2 libsdl-ttf2.0-0 libsmpeg0 libtimedate-perl liburi-perl libwww-perl menu-xdg perl-suid python2.4-pysqlite2 scribus tuxmath tuxpaint tuxpaint-data tuxpaint-stamps-default vorbis-tools xaos
``` The first two commands will make sure you have Ubuntu installed. The second will attempt to remove Edubuntu.

---

### Post by Gordon Farmer on 2006-07-14
Uuuummmmm, in that case, my bad...

---

### Post by madelman on 2006-07-14
This is why  I like this. Thank you for your quick response. Based on aysiu's response I would go for aptitude, anyway this is a new fresh installation and thank you for your help I will be reinstalling and apply ubuntu. BTW this is at home and I am trying to have my family using ubuntu and see how it works for them.

---

### Post by aysiu on 2006-07-14
Why are you reinstalling? Paste into the terminal those commands I gave you earlier.

---

