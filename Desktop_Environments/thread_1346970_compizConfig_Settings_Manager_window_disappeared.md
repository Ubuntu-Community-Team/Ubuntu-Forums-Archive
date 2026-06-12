---
title: "compizConfig Settings Manager window disappeared"
date: 2009-12-05
forum: Desktop Environments
---

### Post by beyossi on 2009-12-05
Hi,

 installed compizconfig-settings-manager, trying to configure translucency. then, after playing around the CompizConfig Settings Manager window becomes not-visible and I can't access it. when starting the application I can see it is on the desktop but since it is not visible I can't do any configurations.

Please help. will  re-installation will help here?

Thanks

---

### Post by alienclone on 2009-12-05
how can you see it if it isnt visible???

sounds like it is on another desktop maybe? try switching workspaces after you open it and see if it is hiding there.

---

### Post by beyossi on 2009-12-05
I see its shape on the small "DESK 1" at the right bottom of the desktop. I even able to drag the window (guessing the location of the title bar).

---

### Post by lrcaballero on 2009-12-05
If nothing works, perhaps you might want to consider uninstalling it and installing it again from the terminal.

CODE:

sudo apt-get remove ccsm (compiz configuration settings manager)

sudo apt-get install ccsm

just a thought!

Luis

---

### Post by beyossi on 2009-12-05
i gave it a try.
apt-get remove compizconfig-settings-manager
then 
apt-get install compizconfig-settings-manager
it didn't help.

I tried:
apt-get purge compizconfig-settings-manager
then restarted the PC, then:
apt-get install compizconfig-settings-manager
But it didn't help neither.

It looks like I set the ccsm as transparent or something like that, and it is written somewhere in a configuration file which I don't know which it is.

---

### Post by beyossi on 2009-12-05
looks like i just solved it.
system->preferences->appearance->visual effects->none

since then I can see all the windows.

Thanks all

---

### Post by lrcaballero on 2009-12-05
I have nothing else to suggest sorry!!!! Just be patient the answer will come in a bit of time!! make sure you save your thread tittle so that if you have to leave, when you come back just go straight to quick search and track down your thread and responces......

good luck

:popcorn:

Luis

---

### Post by ajgreeny on 2009-12-05
It sounds as if your system can not run compiz so perhaps there is no point having cssm installed.

What hardware have you got, particularly the graphics card?

---

### Post by beyossi on 2009-12-06
from hwinfo command:

  Hardware Class: graphics card
  Model: "Intel VGA compatible controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2e32 
  SubVendor: pci 0x1462 "Micro-Star International Co., Ltd."
  SubDevice: pci 0x7592 
  Revision: 0x03


anyway, please note that I fixed it out as mentioned three posts above.

Thanks

---

