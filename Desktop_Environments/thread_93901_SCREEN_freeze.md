---
title: "SCREEN freeze"
date: 2005-11-23
forum: Desktop Environments
---

### Post by petri on 2005-11-23
When trying to chance my SCREEN resolution (?) from 1600 x 1200 to 1024 x 768 or anything else the OS freezes. Not reacting on anything only to the powerbutton
I have XP1800+, Asus A7V266-E and ATI AIW 8500.
Ubuntu as the only OS on the hd, no other hd in my pc.
First I had 5.04 OS and there I could chance the resolution but not in 5.10. ATI's site says I already have the latest drivers.

---

### Post by aysiu on 2005-11-23
Maybe... ```
sudo dpkg-reconfigure xserver-xorg
```?

---

### Post by petri on 2005-11-23
yes, done that and everything seems to be ok. but the machine won't start as it's supposed to :confused:

---

### Post by squirrelyosis on 2005-11-23
Install the nvidia or ati drivers.  This helped me Ubuntu would freeze randomly forcing me to reboot, then i install the Nvidia drivers and now it works like a charm.  Search the forum for a howto.

---

### Post by petri on 2005-11-23
done searching and found it att: [http://help.ubuntu.com/starterguide/C/faqguide-all.html#installatidriver](http://help.ubuntu.com/starterguide/C/faqguide-all.html#installatidriver)

but got problems directly (Synaptic went well):
sudo depmod -a ; sudo modprobe fglrx
FATAL: Error inserting fglrx (/lib/modules/2.6.12-10-386/volatile/fglrx.ko): Operation not permitted


what does that mean?

---

