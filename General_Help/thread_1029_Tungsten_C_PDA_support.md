---
title: "Tungsten C PDA support"
date: 2004-10-17
forum: General Help
---

### Post by nburns on 2004-10-17
Hey, 
  I just picked up a Palm Tungsten C online the other day, and I was wondering what my support options are?

What do I need to be able to sync?
Can I sync via wifi?

---

### Post by adbak on 2004-10-18
Good luck getting GnomePilot to sync with your pda, it didn't detect my Palm Zire 31 no matter what I tried.  You can definitely sync with USB and serial port, and IR too, I forget what the fourth option is.

---

### Post by javaman on 2004-10-18
try using /dev/ttyUSB1.  That works for my Zire 71.

---

### Post by bartleby on 2004-10-18
I use a palm-based Sony Clie to sync with Evolution via Gnome Pilot and it works like a charm. In the setup, where it says /dev/pilot, try entering /dev/ttyUSB0, then after the setup is finished, restart Evolution. I also find that when using Evolution that after you've hit the sync button on the pda you have to click Tools&gt;Pilot Settings in Evolution. Presumably this starts Gnome Pilot. If /dev/ttyUSB0 doesn't work, try /dev/ttyUSB1 etc. as different pdas use different ports.

When you first sync with Evolution make sure the conduits are set to write from pda to computer, otherwise you'll end up with multiple identical entries on the pda. After the first sync you can set conduits to syncronise.

Hope that helps.

---

### Post by nburns on 2004-10-18
Sounds easy enough.  It's coming in today, so I'll try this later on.  Thanks for the help.

---

### Post by adbak on 2004-10-18
Thanks for your help, guys, but still no luck synchronizing my Palm Zire 31.  I tried /dev/ttyUSB0 through ttyUSB5 to no avail.

---

### Post by pyx on 2004-10-20
Hi,
did you load the modules visor and usbserial?
(
sudo modprobe usbserial
sudo modprobe visor
)
You may look into /var/log/messages for additional informations what goes wrong, if this doesn't work..

---

### Post by kaput on 2004-10-25
I changed the "Timeout" setting from 2 to 100 and it worked like a charm for my Treo. The problem seems to be too short of a window. Hope it helps!

---

