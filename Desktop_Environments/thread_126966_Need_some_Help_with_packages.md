---
title: "Need some Help with packages"
date: 2006-02-07
forum: Desktop Environments
---

### Post by outlawtanker on 2006-02-07
I need some help installing codecs for totem and rythmbox that will enable them to play mp3's. I haven't been able to locate the codec folders, although I did manage to install the w32 codecs in apt-get. any help would be much appreciated. :p

---

### Post by RAOF on 2006-02-07
You need to get the "gstreamer0.8-plugins-universe" and "gstreamer0.8-plugins-multiverse".  These include all the codecs that rhythmbox/totem can use.  A search in Synaptic should find you these packages.  If it doesn't, you might need to enable the Universe/Multiverse repositories.  Try the first link in my sig.

---

### Post by outlawtanker on 2006-02-08
The only package I found was a regular package, neither universe or multiverse, although I do have both of those enabled in every category. I installed the package anyways, it was the exact same name without the multi/universe appended. Now, my wma files that used to play are no longer even recognized, now they are all text files, mp3, wma, and I haven't checked my waves yet. but now everything is all buggered up.

---

### Post by outlawtanker on 2006-02-08
ok, that was weird, I uninstalled the package, and now everything works fine. strange.:-D :-D

---

