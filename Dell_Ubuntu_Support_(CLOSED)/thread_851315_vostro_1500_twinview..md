---
title: "vostro 1500 twinview."
date: 2008-07-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by hetcxp on 2008-07-06
hi, my problem is that when i connect the tv or the crt monitor, for both devices i can only use 640x480 as resolution but the laptop monitor keep using 1280x800 and neither can change the laptop monitor nor the tv or crt monitor resolution to make both the same.

my question is, how do i do to add new resolutions to the tv, crt or laptop monitor configuration?

i've added extra resolutions including the subsection display to the xorg.conf screen section but they doesn't appear in monitor resolution or in nvidia xserver configuration.

i'm using hardy.

sorry about my english.

---

### Post by saru411 on 2008-07-06
I'm not sure what "Twinview" is but I'll attempt to help. I'm assuming you are using a Nvidia Graphics card. Goto System>Administration>Synaptic Pagage Manager and search for nvidia settings. Install this package. Now goto terminal Applications>Accessories>Terminal and type in sudo nvidia-settings. Now goto X Server Display Configuration. Click the Detect Displays button and you should see the current displays that are connected to your computer. Now click on the display in the Layout box that you wish to configure. Chose the Resolution that you like and then click Save to X Configuration File.

All should be working after this but you might have to restart X server...this can be done by holding Ctrl + alt + Backspace. I hope all ends well, Good Luck

---

