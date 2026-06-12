---
title: "Nautilus slow to displaying large networked directory"
date: 2010-01-14
forum: Desktop Environments
---

### Post by rebeltaz on 2010-01-14
I have a drive that I am sharing over SAMBA that has a directory with 3100 files in it. When I try to access that directory through Nautilus, it takes several minutes to load and display the directory - if it ever does at all. I can go to terminal and ls that same directory and, sure, it takes about 10 to 20 seconds to start displaying the contents - but that is a lot better than Nautilus does. 

This same drive used to be in a WindowsXP system that was shared over the same network. At that time, Nautilus would display the same directory in the 10 to 20 seconds that terminal gives. 

I can live with simply accessing that directory through terminal (I actually prefer to use terminal when I can), but I would still like to know why Nautilus is reacting the way that it is.

---

### Post by FlyingBuzz on 2010-01-14
Nautilus gets much information about each file when terminal just shows the list of the files. That's the reason for bad perfomance I think.

---

### Post by neednewlaptop on 2010-01-14
Maybe you can try to change nautilus preferences to never show preview for files on network.

---

### Post by rebeltaz on 2010-01-22
> **neednewlaptop said:**
> Maybe you can try to change nautilus preferences to never show preview for files on network.

They already are set to Local Only, but I even tried Never and I still have the same problem...

---

