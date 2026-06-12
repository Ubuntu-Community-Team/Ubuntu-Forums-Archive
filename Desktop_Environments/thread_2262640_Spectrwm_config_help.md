---
title: "Spectrwm config help"
date: 2015-01-26
forum: Desktop Environments
---

### Post by Windobu on 2015-01-26
I installed spectrwm with ```
 sudo apt-get install spectrwm 
``` and it installed successfully. However when I try and make a change to either /etc/spectrwm.conf or ~/.spectrwm.conf, and log into the WM with the default login manager, or by executing ```
 startx 
``` the config file doesn't seem to be working. Though, it worked fine when I was using Arch. Any tips? Should I install from source instead?

---

### Post by ibjsb4 on 2015-01-27
You didn't say what display manager you are using.

Startx should work fine and the arch wiki tells how to create an ~/.xinitrc.
[https://wiki.archlinux.org/index.php/spectrwm#Starting_spectrwm](https://wiki.archlinux.org/index.php/spectrwm#Starting_spectrwm)

also
[https://wiki.archlinux.org/index.php/xinitrc](https://wiki.archlinux.org/index.php/xinitrc)

---

### Post by Windobu on 2015-01-27
> **ibjsb4 said:**
> You didn't say what display manager you are using.

Startx should work fine and the arch wiki tells how to create an ~/.xinitrc.
[https://wiki.archlinux.org/index.php/spectrwm#Starting_spectrwm](https://wiki.archlinux.org/index.php/spectrwm#Starting_spectrwm)

also
[https://wiki.archlinux.org/index.php/xinitrc](https://wiki.archlinux.org/index.php/xinitrc)
That's not the issue. The problem is that no matter how I change the config file, the changes don't apply. Thanks for the help anyways, I may just switch to a different WM

---

