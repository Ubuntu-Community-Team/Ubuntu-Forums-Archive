---
title: "nvidia-settings wont detect primary laptop display"
date: 2011-03-29
forum: Desktop Environments
---

### Post by youngmit on 2011-03-29
I'm using a Dell laptop with an nVidia Quatro card. I recently plugged in an external display and set it up rather successfully using the nvidia-settings utility. After unplugging the monitor and starting the computer back up, the boot process appears on the laptop's display, then once Ubuntu gets into X and to the login screen, everything goes away. Pluggin in the external monitor shows that all of this is being sent to the external. Opening the nvidia-settings utility again shows only the external display, but not the laptop display itself. Clicking "detect displays" does not detect the primary laptop monitor, which is worrisome. 

I tried running the nvidia-config tool to generate a new x config file, but that didnt work. Does anyone have any ideas as to why the laptop monitor cant be detected? Ive tried messing with the function key on the laptop which changes the external monitor mode to no avail. In fact im not sure if that is doing anything at all.

---

### Post by rianquinn on 2011-10-17
dump.... same problem here

---

### Post by youngmit on 2011-10-21
figured it out. Apparently the card was unable to detect the ESID of the laptop screen, so it failed whenever it entered a video mode more advanced than throwing stuff at the device and hoping it shows up. Found the ESID in windows, and manually inserted it via xorg.conf. Yikes!

---

