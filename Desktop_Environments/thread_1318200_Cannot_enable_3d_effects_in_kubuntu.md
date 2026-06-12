---
title: "Cannot enable 3d effects in kubuntu"
date: 2009-11-07
forum: Desktop Environments
---

### Post by Romanrp on 2009-11-07
I am dualbooting ubuntu and kubuntu (both 9.10 and both are 64bit)
I can run 3d effects fine on ubuntu but I cann't seem to get them working on kubuntu.
Everytime I try to activate them it comes up with "check your xorg configuration".
I have downloaded all the 185 nvidia drivers and it still doesn't work.
When i click on the propertiary (hardware) drivers-and click activate the driver-nothing happens.
My card is nvidia geforce g102m.
help please?

---

### Post by Romanrp on 2009-11-07
anyone?

---

### Post by Romanrp on 2009-11-07
bump

---

### Post by prokennexusa on 2013-03-17
The solution for anyone having this issue:razz: , simply remove the compizconfig-backend-kconfig package:

```
sudo apt-get remove compizconfig-backend-kconfig
```

and now everything is ok.

---

### Post by overdrank on 2013-03-17
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

