---
title: "PCManFM not loading"
date: 2013-09-07
forum: Desktop Environments
---

### Post by matt_w2 on 2013-09-07
Hi All,

I recently upgraded my Lubuntu 12.04 box to 12.10, then 13.04. It seemed to go reasonably well, however PCManFM no longer loads. If I VNC into the machine (or connect a monitor to it) I can get a desktop up, but with no background image and if I click on the PCManFM icon nothing loads.

I attempted to run it via a terminal, and got the following:

```
pcmanfm: error while loading shared libraries: libmenu-cache.so.1: cannot open shared object file: No such file or directory
```

As far as I can tell libmenu-cache.so.1 is part of libmenu-cache1, which no longer exists in 13.04 - I did grab a .deb of it from 12.04 and installed it but it made no difference, PCManFM didn't get an error anymore but it still wouldn't load (Not that I was expecting it to). I've tried removing then installing as many of the lxde and lubuntu-desktop packages as I can find, but still no joy. I suspect there's something from 12.04 still floating around on the system somewhere but I've no idea what.. does anyone have any suggestions? I have a feeling I could do with reinstalling the entire desktop 'experience' but I can't see an easy way to do this..

---

### Post by mc4man on 2013-09-08
Were you previously using pcmanfm from a ppa in 12.04/.10?
What's this show
```
apt-cache policy pcmanfm
```

You could try a 
sudo apt-get purge pcmanfm
then update sources & re-install

---

