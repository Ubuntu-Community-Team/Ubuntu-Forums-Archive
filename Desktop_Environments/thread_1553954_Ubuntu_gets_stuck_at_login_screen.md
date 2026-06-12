---
title: "Ubuntu gets stuck at login screen"
date: 2010-08-15
forum: Desktop Environments
---

### Post by user328 on 2010-08-15
I've tried searching the forums, but that didn't help. Pretty much what happened was I installed ubuntu 10.04 32bit version, rebooted my computer, try to login, and I am not able to since I can not even use my mouse or keyboard, it's stuck.
 
Then, I reboot, and it gets stuck at not even loading to the login screen.
 
Could someone have a solution to this?
 
My system specs:
 
AMD Phenom II x4 955
GA-770TA-UD3
ATI Radeon HD 5750
4GB DDR3 Ram
WD Blue 640GB HDD
 
Thanks everyone.

---

### Post by jamessimo on 2010-08-16
> **user328 said:**
> I've tried searching the forums, but that didn't help. Pretty much what happened was I installed ubuntu 10.04 32bit version, rebooted my computer, try to login, and I am not able to since I can not even use my mouse or keyboard, it's stuck.
 
Then, I reboot, and it gets stuck at not even loading to the login screen.
 
Could someone have a solution to this?
 
My system specs:
 
AMD Phenom II x4 955
GA-770TA-UD3
ATI Radeon HD 5750
4GB DDR3 Ram
WD Blue 640GB HDD
 
Thanks everyone.

Hey User! I had this same problem. I believe it happens because of missing or damaged sound drivers (I broke mine first time round trying to get alsa to pickup my old sound card). 

This should fix your problems; [http://www.linuxforums.org/forum/ubuntu-help/86328-ubuntu-startup-freeze.html](http://www.linuxforums.org/forum/ubuntu-help/86328-ubuntu-startup-freeze.html)

---

### Post by user328 on 2010-08-17
> **jamessimo said:**
> Hey User! I had this same problem. I believe it happens because of missing or damaged sound drivers (I broke mine first time round trying to get alsa to pickup my old sound card). 

This should fix your problems; [http://www.linuxforums.org/forum/ubuntu-help/86328-ubuntu-startup-freeze.html](http://www.linuxforums.org/forum/ubuntu-help/86328-ubuntu-startup-freeze.html)

Thanks fore replying. But where would I type this

```
acpi=noapic
```

and this,

```
snd-intel8x0=off
```

---

### Post by jamessimo on 2010-08-17
> **user328 said:**
> Thanks fore replying. But where would I type this

```
acpi=noapic
```

and this,

```
snd-intel8x0=off
```


[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

