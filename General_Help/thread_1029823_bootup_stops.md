---
title: "bootup stops"
date: 2009-01-03
forum: General Help
---

### Post by dougleduck on 2009-01-03
For a while I've had the problem that the system stops during boot up. When I start in safe mode (or whatevr the mode is) it happens when it gets to 

* configuring network interfaces

The only way to continue is to do ctrl-alt-del (randomly discovered this).

Then startup is mostly fine. I have a problem with connecting to my network after logging in ( I have to manually eject my PCMCIA card a couple of times before it will connect to my router) though I suspect this may be unrelated as it developed after the above mentioned problem.

Thanks for any help.

---

### Post by dougleduck on 2009-01-04
bump

---

### Post by dougleduck on 2009-01-05
bump again. if anyone needs more info please ask, not sure what I should be providing.

---

### Post by dougleduck on 2009-01-07
bump

---

### Post by Jameshardy88 on 2009-01-07
i seem to be having te same problem though my computer eventually re-sets rather tan eventually booting

---

### Post by adamlau on 2009-01-07
Sounds like a case of a faulty slot connection. DeoxIT exposed contacts and keep the card pressed into the slot during boot time. The next time you successfully log in to your account, run:

```
 dmesg > ~/Desktop/dmesg
```

and review the dmesg file for clues. Good luck :) .

---

