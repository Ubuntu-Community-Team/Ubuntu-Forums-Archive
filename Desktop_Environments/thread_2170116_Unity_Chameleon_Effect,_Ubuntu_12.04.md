---
title: "Unity Chameleon Effect, Ubuntu 12.04"
date: 2013-08-24
forum: Desktop Environments
---

### Post by cody4 on 2013-08-24
Does anyone know how to make Unity Launcher color changes permanent in Ubuntu 12.04? The custom color I've set through My Unity only lasts until the next reboot.

I know there have been threads on this topic before, but I was wondering if there was any new progress with this issue.

Thanks!

---

### Post by nenadlatinovic on 2013-08-25
Not sure if i understand, but the chameleon color changing is supposed to change according to background. Or you want to have a permanent launcher color regardless of the background?

---

### Post by Frogs Hair on 2013-08-25
From what I find MyUnity was pulled from the 12.04 repository and I'm guessing it no longer works properly.

---

### Post by cody4 on 2013-08-25
Thanks for your replies guys.

> Not sure if i understand, but the chameleon color changing is supposed  to change according to background. Or you want to have a permanent  launcher color regardless of the background?
I would like to have a permanent custom color regardless of the background.

> From what I find MyUnity was pulled from the 12.04 repository and I'm guessing it no longer works properly. 				
Yeah that's right, however I've tried setting a custom color with ccsm and unsettings as well but the color still reverts on reboot, when background is changed, etc.

---

### Post by mc4man on 2013-08-26
There are 2 bugs involved here, both quite fixable but neither has been officially.
I have a repaired unity build in this ppa
[https://launchpad.net/~mc3man/+archive/color-fix](https://launchpad.net/~mc3man/+archive/color-fix)

---

### Post by cody4 on 2013-08-26
> **mc4man said:**
> There are 2 bugs involved here, both quite fixable but neither has been officially.
I have a repaired unity build in this ppa
[https://launchpad.net/~mc3man/+archive/color-fix](https://launchpad.net/~mc3man/+archive/color-fix)

Brilliant! It worked perfectly. 
I've been looking for a solution to this problem for ages, and I lacked the expertise to fix it myself.
Thankyou very much.

---

### Post by mc4man on 2013-08-27
Glad you could make use of it, myself always used black as the custom color & wasn't going to wait for any official fix which never may come.

There is a 'companion' ppa for 12.04 that fixes scale  to pick all windows from all workspaces, again I gave up trying to convince the powers to be that my fix addressed all concerns & just decided to ppa it.
If using please read ppa description carefully

[https://launchpad.net/~mc3man/+archive/fixing-scale](https://launchpad.net/~mc3man/+archive/fixing-scale)

In both cases will keep the ppa's up to date as needed

---

