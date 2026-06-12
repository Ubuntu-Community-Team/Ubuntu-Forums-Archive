---
title: "EPSXE problems"
date: 2006-10-23
forum: Gaming &amp; Leisure
---

### Post by DiJEH on 2006-10-23
I managed to get EPSXE working finally but it seems to run far too quickly and lacks sound. In the menus when I click config nothing happens.. Anyone got any ideas how to get to it so I can config them?

The reason I need to config them is the entire game runs twice as fast as it should and has no sound.. but otherwise it works perfectly.


Edit : I managed to get the sound and video working correctly if I use Pete's MesaGL driver 1.68 but then it stops reacting to my keyboard.. where as before it worked fine..

---

### Post by tarobs on 2006-12-21
Have you tried playing around with the configuration of your ePSXe video plugin? Yours must be set to the "fast" general setting (or something similar). You can access the config menu on the epsxe window through Config>Video, then select configure and play around with the settings.

---

### Post by EddM on 2006-12-21
Set the FPS limit to 50, and make sure "FPS Limit" is actually enabled.

---

### Post by rejser on 2006-12-21
all the files in the plugins file you download aren't supposed to go into the plugins directory. Maybe it was that, missed that myself, the files starting with cfg should go in the cfg folder.
For example cfgPeteMesaGL or cfgPadJoy (these should be executable, if not, chmod +x them)

---

