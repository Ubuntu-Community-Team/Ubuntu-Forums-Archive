---
title: "mass install .deb files ???"
date: 2009-03-28
forum: General Help
---

### Post by forcecore on 2009-03-28
how i can install massive collection .deb files, [**here**]("http://www.mediafire.com/imageview.php?quickkey=umdwbzthhzj&thumb=4") is mplayer for example and i want to install these all in one step.

i know that i must not replace newer or older libs but i have all libs manually checked and verified corresponding to ubuntu version with click to click install first time.

i need to create some script inside folder (example is mplayer) that i drag drop to terminal then is should ask password in terminal then GO...

current way: sudo dpkg -i /folderlocation/*.deb causes synaptic error but i need better script, i am really grateful if anyone can help.


*NB: do not ask to me to use some sudo apt installs or something because i only use offline debs*

---

### Post by mcduck on 2009-03-28
If all the packages are installable, "sudo dpkg -i *.deb" will work. If it doesn't work for you that would mean that either some of your packages are corrupted, for wrong Ubuntu version, or you are missing some dependencies.

No script will change that.

---

### Post by forcecore on 2009-03-28
i installed smplayer with qt4 libs and i know that i do not have any of these libs to conflict but synaptic do not list these files what i have installed. ???

---

### Post by Neo_The_User on 2009-03-28
well you could chain all commands togethor with && and... yah. :lolflag:

---

### Post by forcecore on 2009-03-28
> **Neo_The_User said:**
> well you could chain all commands togethor with && and... yah. :lolflag:

A sample maybe?

still i want to know is that synaptic "weather synoptic" drunk that he cannot list installed files ???

UPDATE: looks like quick search is little drunk, if i made full search insynaptics it found these files.

---

