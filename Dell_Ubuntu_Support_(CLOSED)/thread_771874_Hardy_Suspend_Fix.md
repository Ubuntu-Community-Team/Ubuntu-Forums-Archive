---
title: "Hardy Suspend Fix?????"
date: 2008-04-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by syga on 2008-04-28
Just installed Hardy on my dell 1501. Suspend did not work. Did a google search and found a lot of people complaining of this. I remember I had the same problem with Gutsy. With Gutsy, I disabled the restricted ati video driver, then suspend worked.

With Hardy, I enabled the restricted ati video driver, rebooted it. Then, disable the restricted ati video driver. Reboot it. Then finally, enable the restricted ati video driver. 

Now suspend works. I don't know why, but it works. 

Maybe someone with more linux knowledge can figure out why...

---

### Post by Krudtugle on 2008-04-28
How do you enable/disable the ati video driver? Suspend doesn't work for me neither (just installed 8.04).

---

### Post by zagato on 2008-04-28
This worked for me too. I still have an issue with hibernate. Even after performing those steps. System complains about not having enough free memory. Hibernate works fine when the ATI driver is disabled.

---

### Post by zagato on 2008-04-28
Goto System > Administration > Hardware Drivers. From there on things are clear.

---

