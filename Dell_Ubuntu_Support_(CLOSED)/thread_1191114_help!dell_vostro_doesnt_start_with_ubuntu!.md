---
title: "help!dell vostro doesnt start with ubuntu!"
date: 2009-06-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Snug on 2009-06-18
ive installed 9.04 on a dell 1310 and when the login page appears, it doesnt detect nothing, i cant move cursor or write anything. can someone help me?? thanks!

---

### Post by coffeeaddict22 on 2009-06-19
Hi,
What have you tried? 
Some suggestions:
1) Run the install CD, but instead of installing choose the "try Ubuntu" option.  It should run OK like this; however, it should run after install too...
2) when the system boots up, instead of booting into the regular install, try booting into the recovery console.  One of the options there is to "repair my graphics; choose that, and see if that solves it.
3) Does your hardware work?  Has someone tried to give the keys lunch?  Have you used it on a working system?  Can you try that?

---

### Post by ugm6hr on 2009-06-19
USB or PS2 devices?

Some USB devices misbehave, although they should work after X is loaded.

Did they work when you installed it (i.e. in Live mode)?

---

### Post by Snug on 2009-06-19
hardware rules with vista, and now im writing from ubuntu 9.04, but it doesnt detect nothing at the first time, if im luky it function at second start or third...and no usb devices or anything :S

---

### Post by coffeeaddict22 on 2009-06-19
So your hardware doesn't work on initial boot, but if you reboot it does work normally the second or third time?
Can you open a terminal, and type in ```
dmesg
```; have a look through there for when the numbers change; just before then will be the reboot.  Post it back; there's hopefully something about what isn't working.

---

