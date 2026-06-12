---
title: "8 Dec 08 - updates have made my system unstable"
date: 2008-12-09
forum: General Help
---

### Post by tattrat on 2008-12-09
Yesterday (08 Dec 08) I installed the updates which update manager offered me (about 6 or so - but can't remember exactly what they were). Upto this point my system has been rock solid. 

Now when I use my Huawei E220 mobile broadband modem (which upto now has worked like a dream under intrepid), it struggles to connect, and when trying to connect and using it (once I actually succeed) the system eventually freezes, requiring a hard reset. 

On reboot during the splash, the system detects the previous failed shutdown and checks the disk. Often (though not always) the fsck fails and chucks me to a prompt. I then have to type in fsck manually and there are usually numerous error, which get fixed.

I don't know how to begin to fix this. Can I somehow remove the recent updates? Or even diagnose the problem?

Any help would be appreciated.

Intrepid Ibex 32 bit, ati graphics.

---

### Post by Vadi on 2008-12-09
You can go into Synaptic, and check History for which packages were upgraded on that day. Then, go to each package, and force an older version of the said package.

However a better solution would be filing / finding a similar bug report on Launchpad and contributing to fix (if you have time and patience of course)

---

### Post by tattrat on 2008-12-09
Hi, thanks for that; I thought that synaptic must have some sort of history function...

As for searching/reporting bugs, I have both the time and the patience, although both is running out in dealing with this problem. It is a bit difficukt to know 
(for me at least ) exactly what the problem is, as it doesn't seem to leave any traces (that I am aware of)!

---

