---
title: "Playing rmvb in totem/vlc/mplayer"
date: 2008-12-14
forum: General Help
---

### Post by 7raTEYdCql on 2008-12-14
Is there anyway you can play rmvb files in anything else apart from rplayer

---

### Post by hikaricore on 2008-12-14
You'll need to install the w32codecs package:

> sudo apt-get install w32codecs

If you can't install it search around the site for that package and you'll find repos that you can add that will contain it.  I don't have the time atm to go hunting for ya.

---

### Post by eBoxNet on 2008-12-14
Totem do not provide support for RMVB files by default, even the very powerful codec download system provided in Ubuntu by Gstreamer can enable totem to play RMVB files.

But is very easy to add support for RMVB files in totem, you just need to install w32codec pack.

For a standard Ubuntu system (maybe work for other debian base distributions) you just have to do that in a console:

1- Download the w32codec pack:

wget -c [http://packages.medibuntu.org/pool](http://packages.medibuntu.org/pool)
/non-free/w/w32codecs/w32codecs_20071007-0medibuntu1_i386.deb (Note: this is just one command)

2 - After download the package install it:

sudo dpkg -i w32codecs_20071007-0medibuntu1_i386.deb

original post : [http://www.valeriovalerio.org/?p=76](http://www.valeriovalerio.org/?p=76)

---

