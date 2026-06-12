---
title: "No Wi-Fi in KDE"
date: 2009-04-28
forum: Desktop Environments
---

### Post by tacantara on 2009-04-28
I installed the KDE desktop environment, and when I go to use it, it finds all my hardware except for the wireless card.  Does anyone know of a fix for that?  I like the KDE DE but it's useless if I have to revert to GNOME to get wireless capability.

I also installed the Kubuntu package through Synaptic.  It improved the overall operation of KDE (i.e. started recognizing bluetooth) but the wireless issue remains a mystery.

---

### Post by cookie132 on 2009-04-28
I had the same problem for a while. Do you have KNetworkManager installed?

---

### Post by tacantara on 2009-04-28
I installed knetworkmanager, then rebooted, and still nothing.  I guess I was expecting the system to find my wireless card, like it did when I installed ubuntu, but KDE isn't doing that.  What else am I missing here?

---

### Post by Zorael on 2009-04-28
The part of the system that detects your wifi card is still the same, regardless of whether you're running KDE or GNOME.

In what way doesn't it work? Can't find any networks? There are some known bugs where knetworkmanager can't connect to certain networks, but the kernel should still detect the hardware and load wifi drivers *long* before it even begins to think about which desktop environment to load.

You do have the network manager plasma widget added to your panel/desktop workspace, I assume? See [https://wiki.ubuntu.com/JauntyJackalope/ReleaseNotes#Network%20management%20applet%20must%20be%20re-added%20on%20Kubuntu%20upgrade](https://wiki.ubuntu.com/JauntyJackalope/ReleaseNotes#Network%20management%20applet%20must%20be%20re-added%20on%20Kubuntu%20upgrade).

---

### Post by tacantara on 2009-04-29
Ah, yes, the missing link (yes, bad pun intended).  I did not load the Network Manager applet.  Once I got that loaded, I was able to make a few quick clicks of the mouse and wi-fi was established.  Thank you all for the additional input :)  :KS

---

