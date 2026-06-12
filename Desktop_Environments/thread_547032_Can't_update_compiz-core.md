---
title: "Can't update compiz-core"
date: 2007-09-09
forum: Desktop Environments
---

### Post by czepluch on 2007-09-09
I cant update compiz-core . It's says that one update is available, but when I try to install it, it says that the package is installed, but it still says that the same update is available. and if I go to synaptic and look compiz-core is marked automatically for updating, but still cant be updated, and because of that i cant get compiz-extra .

```

E: /var/cache/apt/archives/compiz-extra_0.3.6.1-0ubuntu2_i386.deb: trying to overwrite '/usr/lib/compiz/libbench.so', which is also in the package compiz-fusion-plugins-extra

```
The error code is not totally perfect written. Had to translate it from danish :)

---

### Post by Rupertronco on 2007-09-09
What version of compiz are you running? I'm pretty sure that was a known bug for 0.52 or something in that vicinity.

---

### Post by czepluch on 2007-09-09
> **Rupertronco said:**
> What version of compiz are you running? I'm pretty sure that was a known bug for 0.52 or something in that vicinity.

Where do i see what version im running ?

---

### Post by garthoverman on 2007-09-09
I'm experiencing this same issue. 

My update manager reads 

"From version 1:0.5.2+20070829-0ubuntu1amaranth1 to 1:0.5.2+20070829-0ubuntu1amaranth1 (Size 180KB)"

---

### Post by ryno519 on 2007-09-10
Have you tried removing compiz completely and installing fresh? You could export your settings first just to be safe, but that should work.

---

### Post by garthoverman on 2007-09-10
> **ryno519 said:**
> Have you tried removing compiz completely and installing fresh? You could export your settings first just to be safe, but that should work.
Yes,  I basically ran:
```

sudo apt-get -y remove compiz-core desktop-effects 
sudo apt-get -y remove compiz compiz-gnome 
sudo apt-get -y remove compizconfig-settings-manager 
sudo apt-get -y remove compiz-fusion-plugins-extra
sudo apt-get -y remove compiz-fusion-plugins-unofficial 
sudo apt-get -y remove libcompizconfig-backend-gconf
sudo apt-get autoremove
```

Then did a CTRL+ALT+BACKSPACE

Then I ran:

```
sudo aptitude -y update
sudo aptitude install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-unofficial libcompizconfig-backend-gconf
```

After that, I ran

```
sudo aptitude upgrade
```

And still the same problem remains.

---

### Post by czepluch on 2007-09-10
bump

---

### Post by s57nev on 2007-09-12
> **czepluch said:**
> bump

bump bump

---

### Post by skylinerr34j on 2007-09-15
just remove the repo and that update will disappear..only thing is..u cant update it..

---

