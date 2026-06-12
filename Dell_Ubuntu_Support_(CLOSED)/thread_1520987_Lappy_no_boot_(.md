---
title: "Lappy no boot :("
date: 2010-06-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kamohammed on 2010-06-30
Good day...
I have a Dell Studio 1535 Laptop with Ubuntu 10.04 installed...

Working well and everything until one stormy night I decided to update my graphics drivers... Its an ATi Radeon HD 3450... I used the drivers from ATi site.
(The drivers that came with the fresh install was working well but some games were running like 1 frame every 5 seconds...)

Anyways, due to that upgrade my laptop does not boot. It reaches as far as seeing the purple ubuntu logo at boot, briefly ... before a solid blank screen appears... No Hdd activity... Staring at it for 15 minutes didnt solve it. Rebooting failed too.. Connecting an external monitor didnt do much. (Instead of a blank screen there was a solid purple screen)...

Any assistance will be greatly appreciated... thanks ^^

---

### Post by varunendra on 2010-06-30
Try booting into 'Recovery Mode' (press & hold 'shift' key while the laptop is booting).

There, select dpkg first (repair broken packages). If it does not work, reboot & try again in recovery mode selecting 'failsafeX' mode this time. It should enable you to log in. Then try rolling back the new driver & using the default one.

---

### Post by kamohammed on 2010-07-15
sry for late reply.
Ok I will try this. (didnt try it as yet...)

Will let you know of the results.

Thanks

---

### Post by kamohammed on 2010-07-19
ok did it and it worked! 
Thanks...
I rolled back my drivers to default and it allowed the os to boot. From there I would have to install back proper proprietary drivers and hopefully it should work... if not I know now how to undo it ^_^.

---

