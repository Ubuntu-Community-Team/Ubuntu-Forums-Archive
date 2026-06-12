---
title: "Desktop Effects Not Working Despite 3D Nvidia"
date: 2007-12-30
forum: Desktop Effects &amp; Customization
---

### Post by slim_jimmy7 on 2007-12-30
I am running a dual boot Windows XP and Ubuntu 7.10 Installation on two separate Hard Drives.  1 GB of Ram, Ge Force FX 5200 128 MB Graphics Card with the Restricted Driver Enabled.

I tried to enable desktop effects by going to system->preferences->appearances and changing to Extra and when I do it allows me to click the radio button, but I don't get ANY message after that, it doesn't say that it won't work it doesn't say that it will work.  I go back and I am supposed to see a new Desktop Effects in the Menu and it is not there.

I than tried Synaptics and tried to install the Compiz Config and it will show up in the system->preferences menu under Compiz Config Setting Manager, but when I click on it nothing happens at all.

Any help would be greatly appreciated...  I am new to this so forgive me if I missed something obvious.

---

### Post by b0rka7a on 2007-12-30
so you can't run compiz config settings manager ?
try running in a terminal "ccsm" without the quotes

---

### Post by Forlong on 2007-12-30
Post the output of ```
dpkg -l | grep compiz
``` and use the forum's CODE tag please (# button)

---

### Post by slim_jimmy7 on 2007-12-30
I appreciate all your help, it turns out I used a 3rd Party Repository for the Kiba Dock and I wasn't getting the right version of Compiz. After I axed his repository everything worked fine.

---

