---
title: "Stuck with generic drivers."
date: 2011-12-09
forum: Desktop Environments
---

### Post by Nickolai_Leschov on 2011-12-09
Hello,

I'm stuck with generic drivers on my Pentium 4 (AGP) / ATI Radeon 9600 system. Proprietary drivers worked on Ubuntu 8.04 LTS, but they don't support 10.04.

I would like decent performance on my system, but I would like to be able to use software not-obsolete software (the one in 11.04 repositories is fine with me). What can I do?

Maybe I can use 8.04 as a base and enable installing from newer repositories and PPA's?
Or can I somehow install drivers with decent performance on 10.04?

---

### Post by BC59 on 2011-12-09
Check from here which driver you can install to your 10.04
[http://pkgs.org/ati-driver-rpm-deb-linux-free-download/](http://pkgs.org/ati-driver-rpm-deb-linux-free-download/)
After that you have to install it manually.

---

### Post by mcduck on 2011-12-09
The open-source drivers are the best you can get on a Radeon 9600 on any even fairly new Linux system.

The new versiosn of Ati's proprietary driver doesn't support the card any more, and the old driver versiosn can't run on any new Linux kernels.

Sadly, there really isn't anything you could do about it. Trying to get all the new stuff (and security updates) to 8.04 system is not possible, new stuff depends on other new stuff, in the end you'd either end with the system upgraded to something else than 8.04 (and without the proprietary driver) or a bunch of broken packages and still without new software or security updates.

---

