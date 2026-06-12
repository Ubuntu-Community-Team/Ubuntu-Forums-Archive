---
title: "Ring Application Switcher = big problem!!"
date: 2009-04-16
forum: Desktop Environments
---

### Post by demoneivo on 2009-04-16
Hi, I have a big problem with Compiz applications switchers (SUPER+TAB and SUPER + **** + S)

When i Switch between applications, I suddenly LOG OUT

Is there a solution??

Is it a video problem or something else?

---

### Post by demoneivo on 2009-04-17
UP!

It seems a problem of my ATI RADEON Video Card

Does anybody know something else?

---

### Post by gjoellee on 2009-04-17
As Ubuntu is modified to start Xorg at once it crashes, it will look like you log out when Xorg crashes in most cases. This can be because the driver for your card does not work with the version of Xorg ou are using, or have you installed a driver at all?

However, ATI does not have the best support for Linux. I would like some information about your computer, please post the upout of the following command:
```
uname -a
```

---

### Post by demoneivo on 2009-04-17
Thank's for the answer!

the command uname -a gives me this:

Linux demoneivo-ubuntu 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

Can it help?

P.S: i was on JAUNTY BETA, now with the updates of candidate release it has never crashed

I really hope that the updates have fixed something that was wrong in BETA

---

### Post by Metralha on 2009-04-24
Hi!
I am on ubuntu 9.04 final realease and I have the same problem with Ring Switcher or Shift Switcher...Just make it spin and it logs me out. My card is an ati x1700 and i didnt install any driver.  IS there any solution?

Thanks anyway!

---

### Post by demoneivo on 2009-04-26
I have again the same problem

Sometimes, everything is fine and sometimes it keeps on crashing

I really think that is a problem with ati driversss

We can open a bug signal in Launchpad

---

