---
title: "Ati 8.42.3 on live cd *guide*"
date: 2007-11-10
forum: Desktop Effects &amp; Customization
---

### Post by ronalde on 2007-11-10
Hello all,

I've been strugling to install an ati driver on the live cd and this has never worked out.
Nowhere on the internet is a precise guide how one can install the driver without the need to reboot, but  yesterday i had a sortoff breakthrough. I installed the ati 8.42.3 driver and didn't have to reboot.
This were the steps i followed:

1 - dowload the .run package from ati
2 - run the package and leave everything on default
3 - press "ctrl-alt-f6" (or any other combination to get to the non-gdm-console)
4 - type "sudo killall gdm" to kill the graphic desktop manager thingy
5 - type "sudo rmmod radeon" to remove the driver which the live-cd uses
6 - type "sudo gdm" to launch your graphic desktop manager again

After this I had a lot of fun with my new ati setup, the only downpoint is that in case of power failure you have to do it againt since it's a live cd :(. But i'll be installing ubuntu later this week instead of XP.

All these steps were performed on a Dell Inspiron 9300 with a mobility radeon x300 128 MB

Hope this helps anyone since i couldn't find it online :\,

regards, 

ronald

---

