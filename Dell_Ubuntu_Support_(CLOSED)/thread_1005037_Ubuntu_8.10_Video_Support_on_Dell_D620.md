---
title: "Ubuntu 8.10 Video Support on Dell D620"
date: 2008-12-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by stevehi on 2008-12-07
I have a Dell D620 and a fresh install of 8.10.  Everything seems to be working correctly, good news since I am new at this, except for my screen brightness.  It keeps going to about half brightness on me and I keep setting it back to full and it go right back to half in about 30 seconds.  After a few times of setting it to full brightness, using the function + arrow keys, it stays.  I have check the brightness setting under the display setting and the power management.  Any suggestions??

---

### Post by andreasis on 2008-12-08
Hi stevehi, and welcome to the forum!

Your laptop comes with an ambient light sensor which automatically adjusts the brightness of your screen if you decide to enable this feature.  Ubuntu comes with this feature enabled.

If you would like to disable this feature, type this into a terminal ```
sudo apt-get remove smartdimmer
``` or alternatively you can go to the top panel > System > Administration > Synaptic Package Manager, quick search for smartdimmer and uninstall it from there.

If you later decide that you want this back, just reinstall it by ```
sudo apt-get install smartdimmer
``` or from the Synaptic Package Manager.

Let me know if I can help you with anything else.

[EDIT] I do realize that I sounded a bit too confident on that matter.  Although I am convinced that you have a dimmer on your notebook, this solution may or may not work for you.  It is definitely worth a try, however.  You may want to look at the bios, too, and play around with the settings there.  

Anyways, post your results either way : )

---

### Post by orangedoor on 2009-03-17
Thanks a lot Andreasis. I had the same problem and this seems to have fixed it after a reboot. I tried various other things before like turning off the ambient light dimming in Ubuntu, forget where the hidden settings were. (I have a Dell D610 and no ambient light sensor anyway).

---

