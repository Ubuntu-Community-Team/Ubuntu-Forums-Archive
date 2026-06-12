---
title: "AWN in 7.10"
date: 2007-11-27
forum: Desktop Effects &amp; Customization
---

### Post by jaideep.rayapudi on 2007-11-27
:confused:Hi. I am quite new to Ubuntu but would like to see how I can get Avant window navigator working on my system (Gutsy)

---

### Post by Ub1476 on 2007-11-27
There's no .deb package for AWN, so you have to compile it from source.

1. [Download]("https://launchpad.net/awn/+download") it from Launchpad.

2. Extract it.

3. Open a terminal

4. Make sure you have the required dependencies:
```

sudo apt-get install build-essential automake1.9 autotools-dev libxdamage-dev libxcomposite-dev libgnome2-common libgnome2-dev \
libgnome-desktop-dev libgnome-vfs-dev libgtk2.0-dev libwnck-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev \
libgnomevfs2-0 libgnome-desktop-2 libgnome2-0 libwnck-common python-gtk2 python-gconf gnome-common \
python-dev python-gtk2-dev python-cairo-dev python-gnome2-dev python-gnome2-desktop gnome-panel python-glade2 librsvg2-common
```


5. Install AWN (terminal)

```
cd avant-window-navigator-0.2.1

./configure

make

sudo make install
```

If you want extra applets read [here]("http://ubuntuforums.org/showthread.php?t=624467").

---

### Post by mcduck on 2007-11-27
..or just use the .deb package to install it. You'll find one from here: [http://www.getdeb.net/release.php?id=1621]("http://www.getdeb.net/release.php?id=1621")

---

### Post by staticvoid on 2007-11-27
you should check out the black curves theme.

[http://ubuntuforums.org/showthread.php?t=572019](http://ubuntuforums.org/showthread.php?t=572019)

---

