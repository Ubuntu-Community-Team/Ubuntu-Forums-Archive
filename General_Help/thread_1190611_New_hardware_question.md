---
title: "New hardware question"
date: 2009-06-18
forum: General Help
---

### Post by 6c45 on 2009-06-18
I am about to install Ubuntu 9.2 . I know during the install it will find the installed
hardware but later I may add another hard drive, tv tuner card, firewire card ect.
Can I configure Ubuntu to detect these hardware changes on it's own like Windows
does?

---

### Post by masux594 on 2009-06-18
First of all, 9.04 [jaunty] or 9.10[karmic].. I'm not sure, but i think that when it detects new hardware, it tries to install .. i repeat, i'm not sure but i think he does.. however, if doesen't, there's a lot of command that of course, install compatible hw.. The "weak spot" of ubuntu [IMHO] is the drivers!

Sysc, A

---

### Post by 3rdalbum on 2009-06-18
There's no Ubuntu 9.2. There's 9.04 which you should be using, or 9.10 which is in heavy development and is not suitable for a new user.

Ubuntu doesn't really care what your hardware was yesterday or 5 minutes ago*. If you put in a new piece of hardware, it will try and find a driver for it, and then load the driver.

*If you change graphics card from Nvidia to ATI or vice-versa, and you were using the proprietary driver, then the old driver will complain but you should still be given the option of "failsafe graphics mode" so you can remove the old driver and install the new one.

---

### Post by dcstar on 2009-06-18
> **6c45 said:**
> I am about to install Ubuntu 9.2 . I know during the install it will find the installed
hardware but later I may add another hard drive, tv tuner card, firewire card ect.
Can I configure Ubuntu to detect these hardware changes on it's own like Windows
does?

If whatever hardware you use is supported by the kernel you have, then it will be "detected".

The current Ubuntu version gets kernel updates that have new hardware constantly added to them, old Ubuntu versions only get kernel security updates.

---

### Post by 6c45 on 2009-06-18
That answered my question thanks.

---

