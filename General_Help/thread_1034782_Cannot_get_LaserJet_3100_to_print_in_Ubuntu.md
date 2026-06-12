---
title: "Cannot get LaserJet 3100 to print in Ubuntu"
date: 2009-01-09
forum: General Help
---

### Post by v8volvo on 2009-01-09
Not sure if I'm posting this in the right place -- if there's a more appropriate section to put the post in, please advise...

Just got Intrepid up and running on my folks' older IBM ThinkCentre. Everything works great except the printer. It's an HP LaserJet 3100 all-in-one machine. CUPS recognizes it and acts like it's installed OK, but then when you try to print something it can't do it. It goes into the print queue and gets as far as saying it's "processing", but never spits anything out, the printer readout never registers that there is a job, and some of the time the computer eventually pops up a message that "the printer may not be connected" (presumably due to something timing out).

I've searched the internet and discovered that there is some confusion as to whether or not HPLIP supports the LJ 3100. Anyone know for sure, or aware of a workaround? It's connected with a serial cable to the LPT/serial port on the PC; it occurred to me that perhaps it might work better using a USB-based cable, but that is just a random guess.

Any tips on how to get this thing working? All it needs to do is basic printing, the scanning/fax functionality is not necessary. Are we up a creek and in need of a new unit altogether, or might there be a trick I can try, use a USB cable instead of serial, etc??

Thanks in advance!

---

### Post by v8volvo on 2009-01-09
Any ideas...?

---

### Post by rbmorse on 2009-01-09
Open a browser and type

localhost:631

in the address bar.  From there, go to "manage printers."

Does your printer show on the status page?  If so, what happens when you click on the "print test page" button?

---

### Post by sonu 1807 on 2009-01-09
Follow the steps given here [http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html](http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html)

---

