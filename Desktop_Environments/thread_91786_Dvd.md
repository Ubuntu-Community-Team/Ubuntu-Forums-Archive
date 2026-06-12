---
title: "Dvd"
date: 2005-11-18
forum: Desktop Environments
---

### Post by seismicmike on 2005-11-18
Ok... now.. how do I d/l and install the DVD codecs...


I couldn't find anything in the wiki.

---

### Post by aysiu on 2005-11-18
Do a search at apt-get.org
Download the .deb to your desktop
Then, type this in a terminal:
```
cd Desktop
sudo dpkg -i libdvdcss2.deb
```

---

### Post by ubnoobie on 2005-11-18
even easier.. 

in terminal mode, run
sudo /usr/share/doc/libdvdread3/examples/install-css.sh


you mentioned not finding the info in the wiki.. take a peek here. it's basically the [www.ubuntuguide.org](www.ubuntuguide.org) for breezy.. the "ubuntu 5.10 starter guide". it's linked from the wiki front page and it's also on your system. :)

on the web:
[http://help.ubuntu.com/starterguide/C/faqguide-all.html](http://help.ubuntu.com/starterguide/C/faqguide-all.html)

or in gnome:
system -> help -> ubuntu 5.10 starter guide

the starter guide would have led you here:
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

which has all sorts of info on getting the "non-free" formats working, including dvd playback:
[https://wiki.ubuntu.com/RestrictedFormats#head-cd84b8e23927ccdb4bb55ffd3074687abec0cf3b](https://wiki.ubuntu.com/RestrictedFormats#head-cd84b8e23927ccdb4bb55ffd3074687abec0cf3b)

---

### Post by seismicmike on 2005-11-19
sweet that worked!!! it's a little choppy though, and occasionally the lips don't match the words. Is there anything I can do about this? It's not *bad*, but it is noticeable.

---

