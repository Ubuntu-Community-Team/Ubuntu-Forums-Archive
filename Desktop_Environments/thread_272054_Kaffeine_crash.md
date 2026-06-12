---
title: "Kaffeine crash"
date: 2006-10-05
forum: Desktop Environments
---

### Post by jdunn on 2006-10-05
kaffeine 0.7.1 crashes often during DVD playback on Kubuntu Dapper.  It uses xine.  However, Kaffeine does not crash while playing streeming video, quicktime files, wmv, etc...It only crashes (and frequently) during DVD playback.  Also, KDE KMPlayer (playing DVDs) and Amarok both work without any problems.  I'm at my wits end trying to solve this.

Also, no one can tell me what repository the latest Kaffeine (0.8.2?) is in.  Even if I knew, I'm reluctant to install it because I don't want to break the dependancies for nonfree codecs and stuff.

---

### Post by jdunn on 2006-10-05
bump

---

### Post by jdunn on 2006-10-05
bump

---

### Post by ^Usa^DonkeyPunch on 2006-10-05
I am having the same problem it will play to an exstent but then my will shut down and say KDE CRASH

---

### Post by mtron on 2006-10-10
i compiled version 0.8.2 from source and it works very nice. 

backup your old profile in ~/.kde/share/apps/kaffeine if you wnat to roll back, than delete the channellist and uninstall the old version, and try my checkinstall package 

at your own risk ;) 

it's compiled on a AMD Sempron 3000+ for ubuntu 6.06 with the xine engine only, cause i use it mainly for DVB which doesn't work with gstreamer. you'll need libxine1c2, libxine-extracodecs, w32codecs libdvdcss2 

[http://www.zshare.net/download/kaffeine_0-8-2-ubuntu1_i386-deb.html](http://www.zshare.net/download/kaffeine_0-8-2-ubuntu1_i386-deb.html)

then:
```
sudo dpkg -i kaffeine_0.8.2-ubuntu1_i386.deb
```

---

