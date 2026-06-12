---
title: "Help! X wont start."
date: 2005-01-05
forum: General Help
---

### Post by MoveZig on 2005-01-05
x wont start.  i think its a problem with the nvidia drivers.  below is a picture of the terminal, help would be appreciated.  if it is a problem with the drivers, how would you remove them? (n00b here)

[IMG]http://img.photobucket.com/albums/v305/Move-Zig/DSC00179.jpg[/IMG]

---

### Post by xkcdmagic8 on 2005-01-05
well it says ur nvidia driver isnt found...did u install it properly?

---

### Post by MoveZig on 2005-01-05
it was installed under synaptic, i followed the tutorial

---

### Post by wallijonn on 2005-01-05
chances are you didn't install the correct module:

[http://www.ubuntuforums.org/showthread.php?p=41234#post41234](http://www.ubuntuforums.org/showthread.php?p=41234#post41234) :

```
linux-restricted-modules-2.6.8.1-3-386
Non-free Linux 2.6.8.1 modules on 386

linux-restricted-modules-2.6.8.1-4-386
Non-free Linux 2.6.8.1 modules on 386

linux-restricted-modules-2.6.8.1-3-686
Non-free Linux 2.6.8.1 modules on PPro/Celeron/PII/PIII/PIV

linux-restricted-modules-2.6.8.1-4-686
Non-free Linux 2.6.8.1 modules on PPro/Celeron/PII/PIII/PIV

linux-restricted-modules-2.6.8.1-3-686-smp
Non-free Linux 2.6.8.1 modules on PPro/Celeron/PII/PIII/PIV SMP

linux-restricted-modules-2.6.8.1-4-686-smp
Non-free Linux 2.6.8.1 modules on PPro/Celeron/PII/PIII/PIV SMP

linux-restricted-modules-2.6.8.1-3-k7
Non-free Linux 2.6.8.1 modules on AMD K7

linux-restricted-modules-2.6.8.1-4-k7
Non-free Linux 2.6.8.1 modules on AMD K7

linux-restricted-modules-2.6.8.1-3-k7-smp
Non-free Linux 2.6.8.1 modules on AMD K7 SMP

linux-restricted-modules-2.6.8.1-4-k7-smp
Non-free Linux 2.6.8.1 modules on AMD K7 SMP
```

This is why you're getting: **Failed to load module "GLCore"**

If you have your respositories already all set up, then you can [COLOR=Red]apt-get install linux-restricted-modules-2.6.8.1-4-386[/COLOR] (or whichever kernel you have), then [COLOR=Red]shutdown -r now[/COLOR] to reboot.

---

### Post by MoveZig on 2005-01-06
Thank you, I'm at shcool now so I'll try it when I get home.

---

### Post by MoveZig on 2005-01-06
Thank you, wallijonn, it now works.
Thanks for your help.

---

