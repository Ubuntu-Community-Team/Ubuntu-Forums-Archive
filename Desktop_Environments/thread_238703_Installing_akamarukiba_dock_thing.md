---
title: "Installing akamaru/kiba dock thing"
date: 2006-08-18
forum: Desktop Environments
---

### Post by Crypty on 2006-08-18
Hi, Just wondering how I install this kiba dock thing in ubuntu. I got the tarball from [http://people.freedesktop.org/~krh/akamaru.git/](http://people.freedesktop.org/~krh/akamaru.git/)

I untared it and i'm trying to do ./configure but it keeps saying "No such file or directory"

So I assume i'm doing something wrong. These are the files I have, but I have no idea how to install the dock.

---

### Post by scxtt on 2006-08-18
there's no configure included in the tar, it appears - which is fine ... assuming you have build tools installed, you should be able to just type **make** from that directory - since a Makefile is included ...

---

### Post by Crypty on 2006-08-18
I needed some package to make but got that done. When I do make install I get:

steve@steve-laptop:~/Desktop/akamaru$ sudo make install
Password:
GCONF_CONFIG_SOURCE= \
                gconftool-2 --makefile-install-rule kiba.schemas
Attached schema `/schemas/apps/kiba/options/position' to key `/apps/kiba/options/position'
Installed schema `/schemas/apps/kiba/options/position' for locale `C'
Attached schema `/schemas/apps/kiba/options/elasticity' to key `/apps/kiba/options/elasticity'
Installed schema `/schemas/apps/kiba/options/elasticity' for locale `C'
Attached schema `/schemas/apps/kiba/options/friction' to key `/apps/kiba/options/friction'
Installed schema `/schemas/apps/kiba/options/friction' for locale `C'
Attached schema `/schemas/apps/kiba/options/k' to key `/apps/kiba/options/k'
Installed schema `/schemas/apps/kiba/options/k' for locale `C'
Installed schema `/schemas/apps/kiba/launchers/file' for locale `C'
Installed schema `/schemas/apps/kiba/launchers/position' for locale `C'
install dock /home/steve/bin/kiba-dock
install: cannot create regular file `/home/steve/bin/kiba-dock': No such file or directory
make: *** [install] Error 1

---

### Post by smallville on 2006-08-18
Edit: Posted on wrong thread. sry.](*,) 

But, I'm also curious about this dock...so I'll keep my eye peeled.

---

### Post by scxtt on 2006-08-18
it's erroring out because of the following:
```
install dock /home/steve/bin/kiba-dock
install: cannot create regular file `/home/steve/bin/kiba-dock': **No such file or directory**
```so you'll have to resolve the reason ~/bin/kiba-dock doesn't exist ... it may simply be a case of specifying it in the Makefile ...

---

### Post by Lunar_Lamp on 2006-08-18
This may be of interest:
[http://ubuntuforums.org/showthread.php?t=235643&highlight=kiba](http://ubuntuforums.org/showthread.php?t=235643&highlight=kiba)

I should warn that it's not the most fully featured bar, but it's quite fun if at times a little frustrating.

---

### Post by Crypty on 2006-08-18
Ah so it isn't the best for actual use huh? 

What would you say is the best dock to use if im looking for eye candy as well as usefulness?

---

### Post by Lunar_Lamp on 2006-08-18
Well, kiba is worth checking out - you may like it.  It doesn't need to be installed, so it's easy to remove.

I quite like using a semi custom default dock.

I create a new dock, and put the icons I want onto it,as well as a desktop switcher thing, increase the size to 45pixels, tell it not to expand, make it transparent, tell it to autohide, modify the timing values of the autohide in "configuration editor" so that it gives me instant response.

I haven't found anything that competes with it for usability, and it looks pretty nice too I think.

---

### Post by FedeXX on 2006-09-15
Kiba is pretty nice! :D

But it shows only ten icons, and actually i haven't found a way to dock the kde start menu :P

---

