---
title: "Conky 1.3.1-1 Problems"
date: 2005-12-14
forum: General Help
---

### Post by nb- on 2005-12-14
I get the following error when I try and start Conky 1.3.1-1  installed through synaptics;

Conky: Xft not enabled
Segmentation fault

And doing an "dpkg -i conky_1.3.3-1_i386.deb ..." install of 1.3.3-1 using the deb package from sourceforge, I get this error;

 Conky: can't open '/sys/bus/i2c/devices/0-0050/temp2_input': No such file or directory please fix i2c or remove it from Conky

Any surgestions?

---

### Post by taurus on 2005-12-14
Then why don't you enable it!!!  Run this at the command and add this line in or make sure it doesn't say no,

gedit ~/.conkyrc

and add this line or change the "no" to "yes"

use_xft yes

Then scroll down toward the end of it and remove any line that has i2c in it...

---

### Post by adduds on 2005-12-14
just an aside one of my friends friends helped or did write that :)

---

### Post by mcduck on 2005-12-15
Conky in repos seems to have some problems with xft, so use the one from their website. (it has some more problems, too. for me all it does is segfault ;))

Then edit the conkyrc, and remove all lines about 'i2c' (or better, make them point to right devices, you can find the right ones with 'sensors' command if you have lm-sensors installed and working).

---

### Post by nb- on 2005-12-15
Thanks mcduck thats what i wanted to know :), its working nicely now with hard drive temps as well, only a little way to go untill it does all i want it to...

---

### Post by sysop073 on 2008-05-03
The Xft error actually means the opposite of what taurus said, it's not that use_xft is off, it's that it's on but conky was compiled without xft support.

---

