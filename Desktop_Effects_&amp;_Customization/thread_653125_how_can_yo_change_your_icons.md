---
title: "how can yo change your icons?"
date: 2007-12-29
forum: Desktop Effects &amp; Customization
---

### Post by boboyo on 2007-12-29
first, i would like to know how to put the icons on my laptop the way they are in this video (in the part where its linux)  
[http://www.youtube.com/watch?v=xC5uEe5OzNQ](http://www.youtube.com/watch?v=xC5uEe5OzNQ)

second, i would like to know how i can make the windows get out when i turn the cube. if you dont know what i mean, watch the video on youtube and it is around 2min 45

i am using ubuntu 7.10 and i have ccsm.

---

### Post by jryprt on 2007-12-29
#1 I do not know
#2 Start with [Forlong's Guide](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion#)  
Then look at [This](http://forum.compiz-fusion.org/showthread.php?t=5303) 3d windows is what you what .

When you get to the part about  [ make install ]  do   sudo make install

---

### Post by b0rka7a on 2007-12-29
Hi !

1) You can change your icons by going to System > Preferences > Appearance > Install , select the icons you downloaded (you can download from [www.gnome-look.org](www.gnome-look.org)) and if they don't automatically apply, you can find them in Customize > Icons.

2) To install the 3D windows effect in Gutsy open a terminal and type in the following lines:
```
sudo apt-get install compiz-bcop compiz-dev
sudo apt-get install build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev libgl1-mesa-dev libglu1-mesa-dev libmetacity-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev libgnome-window-settings-dev gitweb curl autoconf automake automake1.9 libtool intltool libxslt1-dev xsltproc
wget -O '3d.tar.gz' 'http://gitweb.opencompositing.org/?p=fusion/plugins/3d;a=snapshot;h=db3c51d6c5c0df268fc1ec29a4264ef3d21dbbb3'
tar -xvvzf '3d.tar.gz'
cd '3d'
make
sudo make install
```
To start this effect open ccsm and enable the 3D Windows under Effects.

Good Luck and Happy New Year! ;)

---

### Post by jryprt on 2007-12-29
For 3d windows
In the Terminal :

#1  sudo apt-get install compiz-bcop compiz-dev build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev x11proto-scrnsaver-dev libxss-dev libxslt1-dev libtool

#2  mkdir -p  ~/compiz/
#3  wget -O /tmp/3d.tar.gz 'http://gitweb.opencompositing.org/?p=fusion/plugins/3d;a=snapshot;h=db3c51d6c5c0df268fc1ec29a4264ef3d21dbbb3'
#4  tar -xf '/tmp/3d.tar.gz' -C ~/compiz/
#5  cd ~/compiz/3d
#6  make
#7 sudo make install
After compiling
Restart compiz and ccsm.

---

### Post by dummyhead3 on 2007-12-29
Oh, je viens de comprendre de koi tu parlais! tu dois installer kiba-dock: [http://ubuntuforums.org/showthread.php?t=554127](http://ubuntuforums.org/showthread.php?t=554127)

---

### Post by hhhhhx on 2007-12-30
are you taking about kibba dock?

---

### Post by ODF on 2007-12-31
dummyhead3 : Est-ce trop demandé des explications sur la différence entre compiz, fusion, extra, kibba dock et Beryl.

Je sais qu'il y a eu combinaison de compiz et beryl qui a fait fusion, mais c'est tout ce que je sais.

Merci bien.

---

### Post by dummyhead3 on 2008-01-03
compiz + beryl = compiz fusion
kiba-dock est un petit application qui remplace la barre avec tous tes fenetres en bas de l'ecran (comme dans le video, quand il/elle joue avec les icones). Pour utiliser kiba-dock, il faut avoir compiz fusion, compiz, ou beryl.

---

### Post by dummyhead3 on 2008-01-03
compiz / compiz fusion / beryl font tous les effects graphiques du video. 
Extra, c'est compiz fuson integre dans ubuntu (mauvaisement selon moi car tu ne peux presque pas le configurer). En fait compiz fusion est preinstalle dans ubuntu gusty, mais il faut une autre application (ccsm) pour le configurer.
Beryl et compiz ne sont plus activement developpes, seulement compiz fusion qui est une fusion des deux.

---

