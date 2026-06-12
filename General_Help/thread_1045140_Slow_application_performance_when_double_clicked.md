---
title: "Slow application performance when double clicked"
date: 2009-01-20
forum: General Help
---

### Post by craftybones on 2009-01-20
Hello,

My company has built a gtk based application for which we have a launcher on the desktop. At one of our installations, whenever this application is launched from the Desktop, on one specific workflow, the CPU usage spikes up to >90% and the system grinds for 15 odd seconds before moving on to the next screen.

The interesting bit is if we run the same application from a terminal, this doesn't occur. The specific install at that site runs Ubuntu 7.04. I know its old but we had to use it for specific reasons.

I have been unable to reproduce this problem anywhere else and because its at a customer site, we can't debug this information easily. I don't know where else to go for help.

We are using the packages:

libgtkmm-2.4-1c2a
libmysql++2c2a
 
On Ubuntu 7.04(2.6.20-generic).

Thank you for your help,

Jayanth

---

### Post by craftybones on 2009-01-29
Update:

This behaviour is also noticed when run from a terminal over VNC, but not observed when the application is run through ssh for instance.

Thank you,

Jayanth

---

