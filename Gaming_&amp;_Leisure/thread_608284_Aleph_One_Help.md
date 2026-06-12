---
title: "Aleph One Help"
date: 2007-11-09
forum: Gaming &amp; Leisure
---

### Post by GearedForWar on 2007-11-09
Ok I'm a Linux newbie and right now hate the Terminal because its not user friendly.  Can anyone tell me where to get the required Libraries, how to install them and Aleph One so I can play Marathon?

---

### Post by Vadi on 2007-11-09
I'm not sure how you expect a terminal to be user friendly.

You want Synaptic when searching for libraries, that's the easiest way. But give me a moment, I'll see what you need for your game.

---

### Post by Vadi on 2007-11-10
Okay, so I downloaded AlephOne-20071103-nolibs.tar.bz2. Right-clciked on it, extracted it, and read the README file, which told me to read INSTALL.Unix.

Searched for the packages I need in synaptics, and used

sudo apt-get install libsdl1.2-dev libsdl-image1.2-dev libsdl-image1.2 libsdl-net1.2 libsdl-net1.2-dev libsdl-sound1.2 libsdl-sound1.2-dev libboost-dev liblua50 liblua50-dev libspeex1 libspeex-dev

Then you just do

./configure
make
sudo make install

---

### Post by Vadi on 2007-11-10
Yeah, so that game, but you need the original data files to play the game. If you have the original CD, you can just copy them over, or go to [http://alephone.cebix.net](http://alephone.cebix.net) where you can get them too (but read the license on them first, since the game originally was a commercial one).

---

### Post by GearedForWar on 2007-11-10
Thanks!

---

### Post by wretchedmage on 2008-02-29
When I copy the alephone file into the scenario directory I get

while initializing preferences (preferences.cpp:1498)
  fatal alert (ID=-1): Please be sure the files 'Map', 'Shapes', 'Images' and 'Sounds' are correctly installed and try again. (csalerts_sdl.cpp:96)

what am I doing wrong?!  I compiled it and now I feel stupid. lol

---

### Post by wretchedmage on 2008-02-29
Nevermind, I figured it out.

---

### Post by shakyone on 2008-04-01
Would you mind posting your solution for others.  I'm sure your not the only one that boned it up.  The forums are the most re-assuring part of using Ubuntu.  Post a tutorial!

Later.

---

