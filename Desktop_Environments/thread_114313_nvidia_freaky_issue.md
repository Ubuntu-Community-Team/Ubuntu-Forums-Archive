---
title: "nvidia freaky issue"
date: 2006-01-08
forum: Desktop Environments
---

### Post by garak on 2006-01-08
After last kernel update, my nvidia settings are gone (I mean: no nvidia logo and low screen resolution).
I first tried to re-install all nvidia related packages, but I got classic error about version mismatching between kernel version and video drivers.
So I falled back to legacy drivers: now my situation is the following:
```

garak@starbase:~$ sudo dpkg -l | grep nvidia
ii  linux-restricted-modules-2.6.12-9-386-nvidia-legacy 2.6.12.4-11                          Non-free Linux 2.6.12 NVIDIA legacy module o
rc  nvidia-glx                                          1.0.7667-0ubuntu25.1                 NVIDIA binary XFree86 4.x/X.Org driver
ii  nvidia-glx-legacy                                   1.0.7174-0ubuntu25.1                 NVIDIA binary XFree86 4.x/X.Org 'legacy' dri
ii  nvidia-kernel-common                                1.0.7667+1                           NVIDIA binary kernel module common files
ii  nvidia-settings                                     1.0-3ubuntu6                         Tool of configuring the NVIDIA graphics driv

``` So, the problem is that X is not starting at boot. But if I login with root and re-launch gdm with "/etc/init.d/gdm restart", X works! :confused: (even with nvidia logo)
I'm very confused. Any help will be very appreciated. TIA

---

### Post by zappa86 on 2006-01-08
If you installed a new kernel the nvidia module may not be in the right place for that kernel. If you go to directory /lib/modules and perform an:
```
ls -l
```
You should see a directory for each kernel in which the modules are kept. You can see if the actual module is in the directory for your new kernel. I know when I have made my own kernel or changed kernels I need to reinstall my driver. That fixes the problem for me.

---

### Post by garak on 2006-01-08
[quote=zappa86]If you installed a new kernel the nvidia module may not be in the right place for that kernel. [/quote] 
Thanks for your try, but it's not my case.
The modules are in place, I can find them in /lib/modules/2.6.12-9-386 that is the current kernel dir.

As I mentioned before, the nvidia drivers are not absolutely non-working, if so I would try some other ways... :(

Any other ideas?

---

### Post by zappa86 on 2006-01-08
so if you do a:
```
lsmod | grep nvidia
```
do you see the module loaded? if its not loaded then:
```
modprobe nvidia
```
also where did you get your nvidia drivers from? was it the nvidia installer from their website or the drivers from synaptic?

---

### Post by garak on 2006-01-12
[quote=zappa86]so if you do a:
```
lsmod | grep nvidia
``` do you see the module loaded? if its not loaded then:
```
modprobe nvidia
``` also where did you get your nvidia drivers from? was it the nvidia installer from their website or the drivers from synaptic?[/quote] 
nvidia module isn't loaded, and modprobe fails saying module not found.
I always installed/removed packages with synaptic.

Now the situation is changed: I can't get nvidia work, even if I restart gdm :|

Tried again to remove legacy drivers and install non-legacy ones, no luck.
Maybe the only solution is to manually install nvidia latest drivers...

---

### Post by garak on 2006-01-15
I definitely resolved installing manually latest drivers.
It was less difficult than it could seem :)

---

