---
title: "Problems copying files needed for .mov"
date: 2006-07-22
forum: Desktop Environments
---

### Post by Sabrage on 2006-07-22
I posted this in the wrong forum... haha.](*,) 

here's the link:
[http://www.ubuntuforums.org/showthread.php?t=115741&highlight=quicktime+sound](http://www.ubuntuforums.org/showthread.php?t=115741&highlight=quicktime+sound)

I'm trying to get mov files to work.... I have sound but no picture.

---

### Post by taurus on 2006-07-22
Sounds like you probably need to install the codecs!  Use Automatix if you wish or if you have universe & multiverse enable, then try

```

sudo apt-get update
sudo apt-get install w32codecs

```

---

### Post by Amaranth on 2006-07-22
Check out [https://wiki.ubuntu.com/SeveasPackages](https://wiki.ubuntu.com/SeveasPackages)

You want to install w32codecs, totem-xine, and totem-xine-firefox-plugin.

---

### Post by Sabrage on 2006-07-22
Thanks guys, but now I'm confused. The advice from the other thread, about making a symlink, it doesn't work?

---

### Post by Amaranth on 2006-07-22
Skip all that, just turn on Seveas' repos and install the packages I said. Actually, the packages you want to install are: totem-xine, totem-xine-firefox-plugin, w32codecs, libxine-extracodecs

---

### Post by Sabrage on 2006-07-22
Thanks Amaranth, but I'm a newbie so how do I turn on Seveas' repos and install the packages? :-k

---

