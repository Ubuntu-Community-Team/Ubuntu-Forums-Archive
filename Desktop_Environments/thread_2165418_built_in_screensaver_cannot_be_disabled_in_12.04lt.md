---
title: "built in screensaver cannot be disabled in 12.04lte"
date: 2013-08-04
forum: Desktop Environments
---

### Post by Mike_McCauley on 2013-08-04
I wish to totally disable the 10 minute blank to black screen saver that is hard coded (some say, anyway...) into the OS.

In "Brightness and Lock", setting the "turn screen off when inactive for:"  to "Never" does not work.

Neither does uninstalling gnome-screensaver.

Neither do any of the MANY "just type this at the command line and it'll  be fixed" remedies that I have tried that are all over the Internet.

This is a plain vanilla install on an ASUS 900a netbook, with everything that Update Manager wanted to install, installed.

All else on the machine works perfectly, including all video functionality.

I had this "feature" successfully disabled on this machine, but I was forced to reinstall due to a huge dependencies mess apparently created by an Update Manager glitch. And honestly, I have no recollection of how it did it back then. But that was probably several hundred updates ago, so these two cases aren't apples to apples anyway.

Thanks in advance for your help.

---

### Post by ibjsb4 on 2013-08-04
This may be what your looking for

[http://ubuntuforums.org/showthread.php?t=2098422](http://ubuntuforums.org/showthread.php?t=2098422)

more here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=disable+screensaver+12.04&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=disable+screensaver+12.04&sa=Search&cof=FORID:9)

---

### Post by ibjsb4 on 2013-08-04
There is also caffeine

[http://ubuntu-tweak.com/app/caffeine/](http://ubuntu-tweak.com/app/caffeine/)

[https://launchpad.net/~caffeine-developers/+archive/ppa](https://launchpad.net/~caffeine-developers/+archive/ppa)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=how+to+install+ppa&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=how+to+install+ppa&sa=Search&cof=FORID:9)

---

### Post by Mike_McCauley on 2013-08-04
The add-on xorg.conf script described in the link toward the bottom of the page did the trick. Thanks!!

---

