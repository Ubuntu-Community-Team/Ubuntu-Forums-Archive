---
title: "Cinnamon and Unity both break on 13.10 upgrade"
date: 2013-10-29
forum: Desktop Environments
---

### Post by embolalia on 2013-10-29
I run Ubuntu on my work laptop (this is allowed, but not supported, by my employer), with Cinnamon as the DE. It's been pestering me for a bit to upgrade from 13.04 to 13.10, so I did. When it came back up from the restart, both Unity and Cinnamon gave me the same thing: My auto-starting Thunderbird window and nothing else. No window management, decorations, panels, etc. No way to open any other programs. From some searching, it looks like there are known issues with Cinnamon 2 and Ubuntu, but dpkg -l shows I have 1.7.4. I'm out of ideas.

XFCE is working, so I can get things done in the mean time, but I'd still like to get this fixed. Any ideas?

---

### Post by Frogs Hair on 2013-10-29
Hello and Welcome

Cinnamon 2.0 breaks Unity, so I suggest purging the PPA if in use and trying the older version in the software-center  [http://news.softpedia.com/news/Cinnamon-2-0-Corrupts-Unity-on-Ubuntu-13-10-390736.shtml](http://news.softpedia.com/news/Cinnamon-2-0-Corrupts-Unity-on-Ubuntu-13-10-390736.shtml)

---

### Post by embolalia on 2013-10-29
Right, I found that. But, at least according to dpkg, I only have 1.7 installed. (Sorry if that wasn't clear.) I haven't used the PPA at all.

---

### Post by Frogs Hair on 2013-10-29
Sorry , that was noted in your post. Try removing Cinnamon and see if you can  log into Unity just to find out if it's cinnamon  related . If you were running Unity in 13.04 I doubt it is graphics related , but I have to ask if you had a proprietary driver installed prior to the upgrade. Cinnamon is in the repository, but not officially supported like E17 and some of the other window managers/DEs  found there.

---

### Post by embolalia on 2013-10-29
Uninstalling Cinnamon made Unity work. Reinstalling Cinnamon didn't make Cinnamon work, but it also didn't break Unity. I have an nVidia card, but I'm using the nouveau drivers.

---

### Post by PocketDog on 2013-10-30
Cinnamon won't work alongside Unity, you can only have one or the other installed. [http://m.theregister.co.uk/2013/10/29/cinnamon_2_0_review/](http://m.theregister.co.uk/2013/10/29/cinnamon_2_0_review/)

---

### Post by Frogs Hair on 2013-10-30
> **embolalia said:**
> Uninstalling Cinnamon made Unity work. Reinstalling Cinnamon didn't make Cinnamon work, but it also didn't break Unity. I have an nVidia card, but I'm using the nouveau drivers.

Was a version of Cinnamon prior to the upgrade ?

---

### Post by deadflowr on 2013-10-30
It's a conundrum.
Cinnamon in the repos is busted because of gnome 3.8.
The Cinnamon ppa has 2.0+ which breaks Unity on Saucy.

If cinnamon is the desktop of choice then the best solution is to ditch unity.
Go with cinnamon-stable from the ppa.

---

### Post by W00ster on 2013-10-31
I'm running the Cinnamon development branch, using the nightly build PPA and it is working great under 13.10.  
See [http://ubuntu-tweak.com/source/gwendal-lebihan-dev-cinnamon-nightly/](http://ubuntu-tweak.com/source/gwendal-lebihan-dev-cinnamon-nightly/)

---

### Post by Frogs Hair on 2013-10-31
The Op is running the 13.10 repository version . 1.74

---

### Post by deadflowr on 2013-10-31
Here's a bug report on the problem
[https://bugs.launchpad.net/ubuntu/+source/cinnamon/+bug/1180638](https://bugs.launchpad.net/ubuntu/+source/cinnamon/+bug/1180638)

this is for the repo version.

---

### Post by Frogs Hair on 2013-10-31
Good to know , most threads have been in regards to 2.0 which affects other releases .

---

