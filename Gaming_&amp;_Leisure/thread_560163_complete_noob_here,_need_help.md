---
title: "complete noob here, need help"
date: 2007-09-26
forum: Gaming &amp; Leisure
---

### Post by joemofo619 on 2007-09-26
ok, i requested a ubuntu cd, got it, rid myself of windows. ok. 
heres where i get lost. and by lost, i mean, out in the middle of rainforest.
i want to install wine. i looked at how to forums, i looked at the wikis, and i looked at the winehq. they all say the same thing, so, can anyone, please, please, help me. and, i mean, step by step, where to go, what to open help on a messenger.
yahoo: joemofo8907
aim: teenflirt619

if i seem to be away, just im me

please, i dont know what it means to open up command prompt (i did with windows) or terminal window, i dont know anything, i feel like a complete noob. thanks, for reading, and help me please. i need to train for a counter strike tourney

thanks

---

### Post by rsambuca on 2007-09-26
To open a terminal window, go to the top left menu bar and select "Applications -> Accessories -> Terminal"

---

### Post by Lacrimstein on 2007-09-26
ok, so open the terminal (command line) by going to Applications->Accessories->Terminal and type the following:

> wget -q "http://wine.budgetdedicated.com/apt/387EE263.gpg" -O- | sudo apt-key add -

> sudo wget "http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list" -O /etc/apt/sources.list.d/winehq.list

then just type in

> sudo apt-get install wine

---

### Post by Lacrimstein on 2007-09-26
ok, in my above post, there is no space between 387EE263 and .gpg, as well as between sources.list. and d/feisty.list

---

### Post by joemofo619 on 2007-09-26
nvm

---

### Post by joemofo619 on 2007-09-26
wow
just wow
i feel so ******* awesome right now
thanks!

---

