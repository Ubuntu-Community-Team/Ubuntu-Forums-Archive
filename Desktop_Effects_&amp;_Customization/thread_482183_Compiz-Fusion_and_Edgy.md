---
title: "Compiz-Fusion and Edgy"
date: 2007-06-23
forum: Desktop Effects &amp; Customization
---

### Post by zero244 on 2007-06-23
Anyway to install and get Fusion to run on Edgy, or is this just for Fiesty.

---

### Post by anatole on 2007-06-24
bump, i cannot update to feisty, but i'd try out compiz fusion too

---

### Post by chadders on 2007-06-24
You can definitely do it on Edgy, I don't know how because I haven't done it yet. Maybe download the source and compile it.

Good luck :).

---

### Post by bittergourd on 2007-06-24
try this guide, compiling from source.  no idea if it works.  good luck with it.
[http://forums.opencompositing.org/viewtopic.php?f=51&t=758#p6435](http://forums.opencompositing.org/viewtopic.php?f=51&t=758#p6435)

-e

---

### Post by remitaylor on 2007-11-03
> **anatole said:**
> bump, i cannot update to feisty, but i'd try out compiz fusion too

bump.  same here.  I cannot upgrade to feisty or gutsy (due to [_this bug_]("https://bugs.launchpad.net/ubuntu/+bug/124406") [[_post_]("http://ubuntuforums.org/showthread.php?t=566216&page=2")]) and would love to get compiz fusion working.

I've been trying for a few days with minimal success.  I seem to have everything compiling properly, but I can't get the right driver working for my ATI Radeon Mobility 9700.  I get it working very wall (with direct rendering and lotsa FPS) but I get white screens or system crashes when I try to run compiz.

incase it helps anyone, here's my current script for downloading and compiling and installing Compiz Fusion ... 

USE AT YOUR OWN RISK ... Tested on fresh installs of i386 Edgy (Desktop)

Best reference: [http://forum.compiz-fusion.org/showthread.php?t=1985](http://forum.compiz-fusion.org/showthread.php?t=1985)

```
#!/bin/bash

# uncomment extra repos and update
cat /etc/apt/sources.list | sed 's/# deb/deb/g' > apt_sources && sudo cp apt_sources /etc/apt/sources.list && rm apt_sources
sudo apt-get update

# package list compiled from compiz fusion wiki & forum post and i added python-dev (was needed to compile compizconfig-python)
sudo apt-get install build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev libgl1-mesa-dev libglu1-mesa-dev libmetacity-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev libgnome-window-settings-dev git-core gitweb curl autoconf automake automake1.9 libtool intltool libxslt1-dev xsltproc libwnck-dev python-pyrex python2.5-dev python-dev
sudo apt-get build-dep compiz

# you might have to run the above before running the below ... i recently had to (the first line of git clones didn't work for me)

# checkout compiz fusion from git (stable branches) and compile and install
mkdir ~/compiz && cd ~/compiz
for lib in libraries/bcop compizconfig/ccsm compizconfig/libcompizconfig compizconfig/compizconfig-python plugins-main plugins-extra plugins-unsupported decorators/emerald decorators/emerald-themes; do git clone git://anongit.compiz-fusion.org/fusion/$lib; done
for lib in *; do cd $lib && git checkout 0.6.0 && cd ..; done
git clone git://git.freedesktop.org/git/xorg/app/compiz && cd compiz && git checkout compiz-0.6 && cd ..
git clone git://anongit.compiz-fusion.org/users/crdlb/fusion-icon
cd compiz && ./autogen.sh --prefix=/usr/local --disable-kde && make && sudo make install && cd ..
export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig
for lib in bcop libcompizconfig compizconfig-python plugins-main emerald emerald-themes plugins-extra plugins-unsupported; do cd $lib && ./autogen.sh --prefix=/usr/local --disable-kde && make && sudo make install && cd ..; done
cd ccsm && make && sudo make install && cd ..
cd fusion-icon && make && sudo make install && cd ..

# now you should be ready to start!
fusion-icon &
```

I'll post back if I ever actually get this working ... I'm currently on my 4th fresh Edgy install, trying to get this working ...

---

### Post by Forlong on 2007-11-04
Compiling from git will make the upgrade even harder.

I'd recommend doing a fresh install of Gutsy.

---

### Post by remitaylor on 2007-11-06
> **Forlong said:**
> Compiling from git will make the upgrade even harder.

I'd recommend doing a fresh install of Gutsy.

Some of us can't.

> **anatole said:**
> bump, i cannot update to feisty, but i'd try out compiz fusion too

> **remitaylor said:**
> bump.  same here.  I cannot upgrade to feisty or gutsy (due to [_this bug_]("https://bugs.launchpad.net/ubuntu/+bug/124406") [[_post_]("http://ubuntuforums.org/showthread.php?t=566216&page=2")]) and would love to get compiz fusion working. ...

I know Compiz Fusion works on my box using Gutsy.  I'm going to try re-installing Gutsy & seeing what drivers get used, copying the xorg.conf, etc ... then I'll see if I can use that setup in Edgy.  (I can install Gutsy, I just can't type for more than a few seconds at a time)


If anyone can help - please post!

---

