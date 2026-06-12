---
title: "Rotating Cube Idea"
date: 2008-04-11
forum: Desktop Effects &amp; Customization
---

### Post by aidave on 2008-04-11
It would be cool if we could hit a key-combination and have the desktop cube do an automatic rotation.  So we could hit that key and watch the cube rotate slowly (a configurable amount), then press a key or button to come back to the closest window.

Just think of the reactions from people seeing your rotating desktop!  :)

---

### Post by aashay on 2008-04-11
I think this is included in the Screensaver plugin in newer compiz builds

---

### Post by aidave on 2008-04-11
Hmm, I dont see it, can you explain where to find it?

---

### Post by Locutus_of_Borg on 2008-04-11
```
sudo apt-get install compiz-bcop compiz-dev build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev x11proto-scrnsaver-dev libxss-dev libxslt1-dev libtool

mkdir -p ~/compiz/

wget -O /tmp/screensaver.tar.gz 'http://gitweb.opencompositing.org/?p=users/pafy/screensaver;a=snapshot;h=6565001eb389fb0d18cfead6030054cc8edc6c5f'

tar -xf '/tmp/screensaver.tar.gz' -C ~/compiz/

cd ~/compiz/screensaver

make

sudo make install
```

---

