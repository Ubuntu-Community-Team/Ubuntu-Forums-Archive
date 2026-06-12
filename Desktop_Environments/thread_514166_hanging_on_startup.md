---
title: "hanging on startup?"
date: 2007-07-31
forum: Desktop Environments
---

### Post by sedi911 on 2007-07-31
hey guys, after adding compiz and kiba-dock to my startup programs in feisty, ubuntu stopped starting up properly. I deleted their launchers from the .autostart folder, but I still do not have the top menu on my desktop. when i press ctrl-alt-f7 to try and see the terminal, it is just a blank screen. I could be terribly wrong, but does this mean that it's not starting up fully?

---

### Post by designwiz on 2007-07-31
hmmm well looks like ur x server has crashed.. try reconfiguring

> sudo dpkg-reconfigure xserver-xorg

make sure u know the video card if you donot knw follow the defaults settings!

P.S It worked for me , hope it works for me

yeh one more thing... since u cannot go to terminal try accesing via the recovery mode

---

