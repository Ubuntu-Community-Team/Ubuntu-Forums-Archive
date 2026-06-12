---
title: "Got SIGSEGV (segmentation fault) in regnum"
date: 2009-05-19
forum: General Help
---

### Post by madmaxou on 2009-05-19
Hi,
i installed regnum online a few days ago [www.regnumonline.com.ar]("http://www.regnumonline.com.ar") and also got to a certain point, but then it says:
```
max@max-desktop:~/regnum$./rolauncher
max@max-desktop:~/regnum$ Saving backtrace to crash_backtrace_4566.log
Got SIGSEGV (segmentation fault)

```
I visited lots of forums but none of them could give me an appropriate answer.
Thanks in advance...
Maxou

---

### Post by nolliecrooked on 2009-05-19
what kinda graphics card do you have dude?

---

### Post by madmaxou on 2009-05-19
max@max-desktop:~/regnum/live$ lshw -C display
WARNING: you should run this program as super-user.
  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: RV350 AP [Radeon 9600]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=32 mingnt=8

hope it's useful

---

### Post by nolliecrooked on 2009-05-19
yeah, I just posted on something similar to this. ati have dropped support for pre 2000 radeons. the opensource ati driver your using is pretty crappy. you can update x.org to 1.6.1, and the xserver ati/radeon driver to the latest version. its slightly quiker, and dosent crap out so much with errors.

---

### Post by madmaxou on 2009-05-19
ok thanks..

---

### Post by nolliecrooked on 2009-05-19
> **madmaxou said:**
> ok thanks..

hah, sorry man that wasnt very clear, but I dont think you wanna have to go through uopgrading xorg when your a noobie :P

---

### Post by madmaxou on 2009-05-19
Where can i find the xservers-common package; thats the one i should upgrade, isn't it? i also didn't manage to get the latest driver from ATI's website.

---

### Post by madmaxou on 2009-05-19
> **nolliecrooked said:**
> hah, sorry man that wasnt very clear, but I dont think you wanna have to go through uopgrading xorg when your a noobie :P

i didn't  mean it ironicaly, i'm grateful for any kind of answer...:p

---

### Post by nolliecrooked on 2009-05-19
> **madmaxou said:**
> Where can i find the xservers-common package; thats the one i should upgrade, isn't it? i also didn't manage to get the latest driver from ATI's website.

the official drivers from ati WILL NOT work with Jaunty. i upgraded my drivers by following the guide at x.org (thats actually their web address). if you wanna upgrade your x.org/driver safely, get in touch with ATi, they where really helpful :)

> **madmaxou said:**
> i didn't  mean it ironicaly, i'm grateful for any kind of answer...:p
lol :P

---

### Post by madmaxou on 2009-05-19
I'm sorry but either i'm blind or stupid but probably both. where is this guide!?? Also on ATI's website there's only a rpm file, which cannot be installed.

---

### Post by nolliecrooked on 2009-05-19
> **madmaxou said:**
> I'm sorry but either i'm blind or stupid but probably both. where is this guide!?? Also on ATI's website there's only a rpm file, which cannot be installed.

the guide is at the bottom of this page for updating the radeon driver;

[http://www.x.org/wiki/radeon](http://www.x.org/wiki/radeon)

but believe me if your a noobie, its best to wait for the update. I onli did it because I couldnt wait :P

if you still HAVE to do it, I will help you via MSN, but its really up to you if you wanna take the risk...

---

