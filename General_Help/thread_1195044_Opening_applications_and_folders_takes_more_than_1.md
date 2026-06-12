---
title: "Opening applications and folders takes more than 10s!"
date: 2009-06-23
forum: General Help
---

### Post by the8thstar on 2009-06-23
Hello all,

I'm having a peculiar problem with folders in Ubuntu 9.04 :  the hard disk is working but it takes up to 10 seconds to open a folder like /Home or Documents for instance. 

Apps are slow to launch too... but my laptop is a Core processor with 2Gb of RAM, so what is the problem here?

---

### Post by the8thstar on 2009-07-23
Bump

---

### Post by jerrrys on 2009-07-23
I once replaced the standard folders with home pictures and as a result it took over a minute to open a folder.  I surmised that nautilus was going thru gigs of pictures to find the right one each time i open a folder.  have you done anything like this?

---

### Post by Fungyo on 2009-07-23
check if something is causing high CPU or HDD usage.
Open a terminal and execute:
```
top
```

look to see if there are any programs using high percentage of CPU and also look at the wa %.
If %wa is high install iotop to see what is writing to your hdd
```
sudo apt-get install iotop
```

have attached a screenshot of top with highlight areas to look at.

by default, both programs list processes with highest usage processes first in descending order.

---

