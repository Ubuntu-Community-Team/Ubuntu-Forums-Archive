---
title: "missing toolbar on 14.10"
date: 2014-12-28
forum: Desktop Environments
---

### Post by dario-iezzoni on 2014-12-28
Good morning fellow forum members,

i'm running ubuntu 14.10 64bits with ubuntu studio installed (dual-boot with win7).

my machine is is a toshiba notebook tecra r850. with intel core i5-2520M CPU@2.5GHz 4Go RAM 
the LSPCI is [IMG]https://www.dropbox.com/s/y32ncpf12dw4tjj/resultat%20lspci.png?dl=0[/IMG][https://www.dropbox.com/s/y32ncpf12dw4tjj/resultat%20lspci.png?dl=0](https://www.dropbox.com/s/y32ncpf12dw4tjj/resultat%20lspci.png?dl=0)

Graphic card is Radeon HD 6450M.

After a few wrong manipulations with my grub (felt like mickey in fantasia...), i managed to get back to my desktop and back-up my /home.

the problem is : i can only get my desktop. i can't access anything else. tty is accessible. ctrl-alt-f1. i tried to reset unity with method here : [http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html](http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html) but no avail.

i'm trying to get gedit open from a terminal (to be in sudo mode) to modify the grub file where i can erase anything related to radeon and i915 and hust have quiet splash and nomodeset. and hopefully get my computer back to normal.

any idea ?

tks in advance !

dario

---

### Post by Bucky Ball on 2014-12-28
Welcome. Ubuntu Studio uses xfce4 so not sure where Unity fits with this. :-k

---

### Post by dario-iezzoni on 2014-12-28
xfce4 is a good start to start my investigations. One thing though (i apologize in advance for my approximate knowledge): if added ubuntustudio while i was on 14.04, then i migrated to 14.10 (ubuntu amd64), should i have i upgraded to ubuntu studio 14.10 (or wait for its eventual appearance ?).

smells like a fresh install of ubuntustudio...

---

### Post by Frogs Hair on 2014-12-28
When adding additional desktops it is only the primary desktop that upgrades. If you started with Ubuntu then that's  the distribution that upgrades. Packages required for other installed desktop environments may also upgrade as needed.  If you use Ubuntu Studio most of the time a clean installation would be a good plan.

---

### Post by Bucky Ball on 2014-12-29
Just a point: 14.10 is supported for nine months, 14.04 LTS is supported for five years (April 2019). If you don't mind upgrading the OS to the next interim release every six months, then 14.10 is no biggie. If you'd rather set and forget for the long haul, then the LTS release is the go. Good luck. 

So you installed Ubuntu Studio with ubuntustudio-desktop from the software centre? I get it now. You had Unity installed with the regular Ubuntu then installed UStudio packages. My mistake. Not sure if that would drag in xfce4. 

If you're wanting to use UStudio, I'd probably go with a clean install. You don't need them both. That can create bloat, conflicts and duplication of apps.

---

