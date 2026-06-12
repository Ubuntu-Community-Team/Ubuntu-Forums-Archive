---
title: "Installing lgeneral data problem"
date: 2005-10-17
forum: Gaming &amp; Leisure
---

### Post by Biased turkey on 2005-10-17
I installed the lgeneral package using Synaptic, now I have to install the lgeneral data.
To do so, I use the lgeneral data installer:  lgc-pg.
That installer expcts the lgeneral package to be installed in /usr/local/share/games/lgeneral but in reality synaptic installed the lgeneral package in /usr/share/games/lgeneral
Is there any way around ?
tia for any help.

---

### Post by bluck on 2005-10-17
[QUOTE=Biased turkey]I installed the lgeneral package using Synaptic, now I have to install the lgeneral data.
To do so, I use the lgeneral data installer:  lgc-pg.
That installer expcts the lgeneral package to be installed in /usr/local/share/games/lgeneral but in reality synaptic installed the lgeneral package in /usr/share/games/lgeneral
Is there any way around ?
tia for any help.[/QUOTE]

try this command: 

sudo ln -s /usr/share/games/lgeneral /usr/local/share/games/lgeneral

kind of a kludge,  but should do the trick.

---

### Post by Biased turkey on 2005-10-18
[QUOTE=bluck]try this command: 

sudo ln -s /usr/share/games/lgeneral /usr/local/share/games/lgeneral

kind of a kludge,  but should do the trick.[/QUOTE]

Thanks a lot for the info Bluck
In fact creating a symlink crossed my mind, but I didn't know exactly how to do and if it would work.
Do you play lgeneral ?

---

### Post by Biased turkey on 2005-10-22
I made the link, it works fine.
thanks herr general

B.T.

---

### Post by bluck on 2005-10-22
glad i could help.

tell ya the truth, never heard of lgeneral :)

---

