---
title: "Upgrade hangs calculating the changes"
date: 2008-04-27
forum: Desktop Environments
---

### Post by elicoten on 2008-04-27
I'm trying to upgrade from Gusty 7.10 to Hardy 8.04 and each time I try the update hangs on "calculating the changes".

When I try again I get the option to do a partial upgrade, which I haven't tried and then the regular updates (now it shows over 600 of them) and the option to upgrade the distribution.

How can I safely upgrade my ubuntu installation? I've had this problem before when I was upgrading to Gusty and I think I got around it using the partial upgrade option but I don't remember exactly what happened last time.

I attach the log files. term.log is empty.

---

### Post by unoodles on 2008-04-27
I had alot of problems getting my upgrade working. In the end i used
sudo do-release-upgrade -m desktop

Hope it helps!

---

### Post by elicoten on 2008-04-28
Yup this solved the problem - thanks a lot.

---

