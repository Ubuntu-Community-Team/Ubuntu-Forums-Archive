---
title: "ubuntu has become slow?"
date: 2009-03-03
forum: General Help
---

### Post by abhilashm86 on 2009-03-03
from yesterday my ubuntu 8.04 has become too slow, the program i select will open slowly, also firefox same effect as it takes time to scroll up and down, all players and files have become slow in performance, please help to restore previous efficiency,

please help and i don't want to re-install ubuntu, i upgraded to 8.10 also. One more is i have eclipse, big softwares, updates and programs, so impossibe to reinstall.....

i want my earlier ubuntu which was fast and awesome, today i felt so disturbed in morning and i din't go to college also :(
please help friends

---

### Post by clarknova on 2009-03-03
Your post is a little shy on details.

What have you tried? What is your RAM usage? Swap? Are your disks using DMA or PIO? What did you install or uninstall right before things got slow? What is top/htop telling you?

Provide some more details and we will be in a better position to help out.

---

### Post by abhilashm86 on 2009-03-04
> **clarknova said:**
> Your post is a little shy on details.

What have you tried? What is your RAM usage? Swap? Are your disks using DMA or PIO? What did you install or uninstall right before things got slow? What is top/htop telling you?

Provide some more details and we will be in a better position to help out.

yea my RAM is 1 GB with dual core processor, 
i have provided htop screenshot below,

---

### Post by abhilashm86 on 2009-03-04
can any one tell how to remove temporary files (like temp in ms), also i just un installed wine, then also no effect in performance.

---

### Post by rylee on 2009-03-04
click on Tools>>Internet Option>>Delete (tab)
You can also check your hard drive for temp ,in your search type Temp or Internet temporary files>>delete all of them

---

### Post by abhilashm86 on 2009-03-04
still firefox is opening web pages too slowly and even other program applications, it just drags and too much irritating, hey can i restore my system to any previous date? tell any solution?

---

### Post by clarknova on 2009-03-04
Looking at your cpu history there is something keeping 1 of your CPU corse occupied. The key will be to watch htop to see what it is. In your screenshot /usr/bin/X is at 42%, which seems high, but if you watch it for a few seconds you should see something going regularly over 90%. This will be your first clue.

Sometimes top will give you insight as well, as it breaks down cpu usage by type.

You have rebooted since yesterday, right?

---

### Post by abhilashm86 on 2009-03-04
> **clarknova said:**
> 

Sometimes top will give you insight as well, as it breaks down cpu usage by type.

You have rebooted since yesterday, right?

yea i rebooted from yesterday, from yesterday after installing downloadthemall option of firefox, system went to that state, i just stopped compiz, now its just recovering............

---

