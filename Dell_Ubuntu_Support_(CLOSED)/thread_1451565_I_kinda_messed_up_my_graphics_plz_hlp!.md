---
title: "I kinda messed up my graphics plz hlp!"
date: 2010-04-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Pabloincarnate on 2010-04-10
I've been using ubuntu on my laptop a while now but not really for gaming so i wanted to try with warcraft 3. The game would start but run very slow and flicker a lot. sum 1 told me that i should use the synaptic package manager to look for stuff relevant to my graphics card. needless to say that made things worse as compiz had stopped working and my laptop started running ubuntu in low graphics mode. 

I have a DELL LATITUDE D600 with a Moblity Radeon 9000 graphics card

These are the packages that i installed
[ATTACH]152864[/ATTACH]

I hope this is enough information

---

### Post by 2hot6ft2 on 2010-04-10
The bottom 2 are installed by default, so leave those and remove the others (the top one and any it requires looks like it may be your graphics driver since it says Radeon and the ones that say fglrx may be required for it). Keeping your fingers crossed the whole time since if you "thought" you installed jocky there may be others you're mistaken about.
Then you may need to reinstall your graphics driver in
System > Administration > Hardware Drivers
(which by the way IS jocky).
 (you may have to reboot into low graphics mode to do it, keeping your fingers crossed)

Next time disable compiz when playing games as both are graphics intensive.

---

### Post by Pabloincarnate on 2010-04-10
Thanks i'll see if this works

---

