---
title: "Problem with Natty Narwhal Ubuntu 11.04 &amp; Radeon ATI Proprietary Driver."
date: 2011-06-08
forum: Desktop Environments
---

### Post by RSims on 2011-06-08
[IMG]http://ubuntuforums.org/images/icons/icon4.gif[/IMG] **Problem with Natty Narwhal Ubuntu 11.04 & Radeon ATI Proprietary Driver.** 
There is a issue with Ubuntu 11.04 Natty Narwhal 64 bit and the compatability with my Radeon ATI Propriatery driver. I have a Radeon HD 4850 PCI Express Video Card. Note: I had no issue with Maverick Meerkat 10.10
The issue that happens, is as soon as I install this driver, I lose all input from my display, and I get "Input not available" on my screen.
Whole screen goes black while the OS works fine in the backround, only as soon as this driver is installed. I've wiped the system twice, and I am sure this is the problem.
 
Let me know what other information you guys may be interested in.
[IMG]http://ubuntuforums.org/images/statusicon/user_offline.gif[/IMG]

---

### Post by RSims on 2011-06-08
bump

---

### Post by misha1983 on 2011-06-19
Although my symptoms are different (see [this thread]("http://ubuntuforums.org/showthread.php?t=1782088")), I also have problems with my Radeon card under Natty.

Since it sounds like it's going to be a while before this issue gets fixed (it's a closed source driver, so only ATI guys can fix this), I'm downgrading back to Lucid LTS.

---

### Post by drgrumbles on 2011-10-03
I don't know if anyone is still looking into this but I have an ATI Radeon HD 5570 and abandoned Ubuntu because it would never work with it.  However, I finally found a discussion that helped me fix my problem.

All I had to do (after installing the proprietary driver again) was install CompizConfig or the Compiz Settings Manager.  

I had trouble with this but after the following three lines in terminal it installed.
```

sudo apt-get update && sudo apt-get upgrade
sudo apt-get install ubuntu-restricted-extras                      
sudo apt-get install compizconfig-settings-manager                      
```

In the Compiz settings manager, I went to the OpenGL option and clicked on it (the item itself rather than the check box next to it) and in the resulting menu I unchecked "Sync To VBlank".  Since then the proprietary driver has worked perfectly. 

Sorry if I was too newb-ish in my description but clear instructions like this are really helpful to newbs (like me, really).

Just want to give credit to a user on here called Mosabama for coming up with the fix involving the Compiz setting and technosysind for getting the compiz settings manager to install properly.

Finally, I can use Ubuntu again!

---

