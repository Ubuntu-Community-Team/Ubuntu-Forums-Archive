---
title: "PCMCIA &quot;failed&quot; (in red) is getting OLD!"
date: 2006-06-01
forum: Desktop Environments
---

### Post by Neobuntu on 2006-06-01
What's the deal? How can I definitively STOP the failed message on boot? I don't even have pcmcia on the desktop nor will I probably install a PCI to PCMCIA card for it. 

I wonder why ubuntu can't tell I have no pcmcia? 

I seems I saw somewhere and as some time a choice on install to do away with pcmcia packages when on a desktop but not on this machine as I've upgraded and did not see this option in the distant past.

Can you help me?  Everything I've tried still pops up red FAILED.

---

### Post by meng on 2006-06-01
I have the same issue. Let me know what you tried so I won't try those things myself. Meanwhile, I have to rescue the system from the x-server crash ...

---

### Post by erimar77 on 2006-06-01
i would follow this.. and disable the pcmcia service


[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

---

### Post by majkmil on 2006-06-01
I had the same problem. Install this and run the prog and turn pcmcia off.

sudo apt-get install sysv-rc-conf
to run sudo sysv-rc-conf

---

### Post by Neobuntu on 2006-06-01
Thank you all very much but I had that installed and the two pcmcia choices only have a check under S for stop so what am I doing wrong? It still says PCMCIA failed!

---

### Post by majkmil on 2006-06-01
I removed the X and all was fixed.

---

### Post by Neobuntu on 2006-06-01
Yep, my bad. I removed the X from the "S" column and IT'S GONE!

No more FAILED (red), and there was much woot.

---

