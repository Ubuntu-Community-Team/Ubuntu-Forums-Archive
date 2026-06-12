---
title: "problem with mplayer"
date: 2005-06-20
forum: Desktop Environments
---

### Post by nephish on 2005-06-20
i cant seem to get mozplugger to bring up the mplayer plugin because i cant get mplayer installed. Heres the deal. 
i have installed the w32codecs, no problem. 
and i have installed vlc installed and it works when i play a movie file on my hard drive but i cant get mplayer installed and vlc or totem (it works too) to play any streaming media from the web. i thought that totem depended on mplayer, but totem works.
nothing comes up. so i thought i would just get the regular mplayer . i have the nerim testing sources in sources.list. but here is what i get when i try to 
sudo apt-get install mplayer-386.
mplayer-386:
 Depends: libavcodeccvs but it is not going to be installed
  Depends: libc6 (>=2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
  Depends: libfontconfig1 (>=2.3.0) but 2.2.3-4ubuntu7 is to be installed
 Depends: libpostproc0 but it is not going to be installed
  Depends: libvorbis0a (>=1.1.0) but 1.0.1-1 is to be installed
 Depends: libxvidcore4 but it is not going to be installed
 Depends: xmms but it is not going to be installed

i either need the mplayer plugin to work with mozilla-firefox, or for VLC to work in firefox or even totem. 
something, anything.. .that will stream video for me from firefox.
any takers ?
thanks.

---

### Post by gil-galad on 2005-06-20
[QUOTE=nephish]i cant seem to get mozplugger to bring up the mplayer plugin because i cant get mplayer installed. Heres the deal. 
i have installed the w32codecs, no problem. 
and i have installed vlc installed and it works when i play a movie file on my hard drive but i cant get mplayer installed and vlc or totem (it works too) to play any streaming media from the web. i thought that totem depended on mplayer, but totem works.
nothing comes up. so i thought i would just get the regular mplayer . i have the nerim testing sources in sources.list. but here is what i get when i try to 
sudo apt-get install mplayer-386.
mplayer-386:
 Depends: libavcodeccvs but it is not going to be installed
  Depends: libc6 (>=2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
  Depends: libfontconfig1 (>=2.3.0) but 2.2.3-4ubuntu7 is to be installed
 Depends: libpostproc0 but it is not going to be installed
  Depends: libvorbis0a (>=1.1.0) but 1.0.1-1 is to be installed
 Depends: libxvidcore4 but it is not going to be installed
 Depends: xmms but it is not going to be installed

i either need the mplayer plugin to work with mozilla-firefox, or for VLC to work in firefox or even totem. 
something, anything.. .that will stream video for me from firefox.
any takers ?
thanks.[/QUOTE]
 You need to get rid of the marillet repositories.  They are compiled for debian, not ubuntu, and do not work correctly.  Stick with the mplayer in the normal repositories and install mozilla-mplayer.

---

### Post by nephish on 2005-06-20
ok, i commented out the nerim line in sources.list.
did apt-get update
good enough.
did sudo apt-get install mozilla-mplayer
couldnt find package mozilla-mplayer
apt-cache search mplayer
nothing relevent.
no mplayer package.
hmmmm.
i do have mozilla-plugin-vlc
but it doesnt work i guess.
am i missing something here?

thanks for the quick response by the way

---

### Post by gil-galad on 2005-06-20
Do you have the universe and multiverse repository enabled?  It is in one of those.

---

### Post by nephish on 2005-06-20
yep, added sources for multiverse
apt-get update
apt-get install mozilla-mplayer
lo and behold....
he he.
didnt even know multiverse existed untill a half hour ago/
thanks a lot

---

### Post by gil-galad on 2005-06-20
glad you got it working :)

---

