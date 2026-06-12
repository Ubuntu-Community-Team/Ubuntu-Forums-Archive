---
title: "F-Spot 0.1.5"
date: 2006-01-16
forum: General Help
---

### Post by marguz on 2006-01-16
All,

Using Breezy Badger you can now have f-spot 0.1.5 !

I found this at [http://www.nabble.com/Re%3A-Ubuntu-Users-t826999.html](http://www.nabble.com/Re%3A-Ubuntu-Users-t826999.html)

I will do a shameless copy and past, I'm just passing this on ;-)

Just do the following:

# apt-get install f-spot
The following NEW packages will be installed:
  binfmt-support libdbus-1-cil libgconf2.0-cil libglade2.0-cil libglib2.0-cil
  libgnome2.0-cil libgtk2.0-cil libmono0 mono-classlib-1.0 mono-common
  mono-jit)

# apt-get build-dep f-spot
The following packages will be REMOVED:
  liblinc-dev
The following NEW packages will be installed:
  build-essential cdbs cli-common dpatch g++ g++-4.0 libbonobo2-dev
  libbonoboui2-dev libexif-dev libgconf2-dev libgnome-keyring-dev
  libgnome2-dev libgnomecanvas2-dev libgnomeui-dev libgnomevfs2-dev
  libgphoto2-2-dev libidl-dev libmono-dev liborbit2-dev libsqlite0-dev
  libstdc++6-4.0-dev mono-mcs mono-utils

# mkdir /usr/src/f-spot ; cd /usr/src/f-spot
# wget [http://ftp.gnome.org/Public/GNOME/sources/f-spot/0.1/f-spot-0.1.5.tar.bz2](http://ftp.gnome.org/Public/GNOME/sources/f-spot/0.1/f-spot-0.1.5.tar.bz2)
# tar -xjvf f-spot-0.1.5.tar.bz2
# cd f-spot-0.1.5
# ./configure; make; make check
# make install

...and the new version's installed in /usr/local/bin/f-spot 

Thanks to Thomas Van Machelen and Daniel Allen-3

F-spot 0.1.5 is sweet!

---

### Post by dada1958 on 2006-01-18
Sweet f-spot 0.1.5 remains crashing when I want to import photos from my camera :confused:

---

