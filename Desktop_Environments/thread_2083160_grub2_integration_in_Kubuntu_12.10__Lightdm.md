---
title: "grub2 integration in Kubuntu 12.10 / Lightdm"
date: 2012-11-11
forum: Desktop Environments
---

### Post by SalsaDoom on 2012-11-11
Hi fellas,

In older versions of Kubuntu which used kdm one could configure the system to allow you to select which operating system or kernel to reboot into from KDE's shutdown menu, by clicking on the restart icon (instead of the text) which would open a menu showing your grub1/2 menu. This was a feature of KDM. Since Kubuntu 12.10 uses LightDM this handy feature doesn't seem possible anymore. Or is it? Anyone know if LightDM supports this or there is a workaround?

Cheers! :)

PS. This [page]("http://ksmanis.wordpress.com/2012/01/29/grub2burg-integration-in-kde/") explains the process for the older versions.

---

### Post by SalsaDoom on 2012-11-14
Answering my own question :)

I have one workaround and one fair solution. Its easy enough to just replace LightDM with KDM. The "workaround" can be used on Unity/Gnome3/Whatever too btw, so its handy if you want to reboot into Windows (until more games come out for Steam for Linux anyway! :) and walk away to get coffee or whatever while the system boots.

I made a quick shell script with
```

#!/bin/bash
sudo grub-reboot "Windows 7 (loader) (on /dev/sda1)"
sudo reboot
```

That boots into Windows. This doesn't change the default permanently, only for the next reboot, so when you reboot windows you'll go back into linux. Note you can also use numbers starting from zero to select a menu item, I prefer to use the name. The command 

```
grep menuentry /boot/grub/grub.cfg
```

Gives you a short list of the names to copy paste. I prefer this as if you mess around with grub (say, adding another OS) it won't change up the orders. Ie, if you select grub-reboot 3 and add something in before that 3 will boot into something else, if you specify the name it won't matter. Just preference here.

Now. I like my properly working KDE shutdown menu so I'll just replace LightDM with KDM and be done with it.

```
apt-get purge lightdm && apt-get install kdm
```

Note that this removes the kubuntu-desktop and may mess up a dist-upgrade later. Just reinstalling that before you run do a dist-upgrade should fix that though.

Now, go to the System Settings -> Login Screen -> Shutdown (tab) -> Boot manager and set "Grub2" on the dropdown and your done.


Cheers!
PS: This [page]("http://edwardhughes.org/2012/11/using-kdm-instead-of-lightdm-in-kubuntu-12-10/") was helpful, but the some of the apt commands were wrong and in my case the -nr command wasn't present, perhaps a bug already fixed.

---

