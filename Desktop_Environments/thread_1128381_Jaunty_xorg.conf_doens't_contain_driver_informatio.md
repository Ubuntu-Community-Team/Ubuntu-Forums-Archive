---
title: "Jaunty xorg.conf doens't contain driver information"
date: 2009-04-17
forum: Desktop Environments
---

### Post by Scabby_al on 2009-04-17
I have one of the older ATI cards that AMD decided to stop supporting and tried to improve performance by playing around with some options and screwed up X by accidentally enabling 'fglrx'. I booted my machine in recovery mode and went to change the x driver back to 'ati' and xorg.conf didn't really have anything in it. I tried xfix and a few other things and can't find a solution.

---

### Post by Fejker on 2009-04-17
Boot into recovery console mode and type the next command:

apt-get remove fglrx*

That should remove all the fglrx things on your computer and when you reboot you should get your X session back. If it doesn't work right away just reboot again and choose "X defaults".

I hope this helps. It did for me as I'm also struggling with 3D support in Jaunty and my ATI HD 3650 mobile card.

---

