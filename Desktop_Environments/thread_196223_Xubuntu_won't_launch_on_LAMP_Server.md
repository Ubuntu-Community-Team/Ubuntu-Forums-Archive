---
title: "Xubuntu won't launch on LAMP Server"
date: 2006-06-13
forum: Desktop Environments
---

### Post by Indifferent on 2006-06-13
I installed a LAMP server from the server disk and everything worked fine. I want a GUI because I am still weaning off of Windows and it would make things easier, so I read someone's suggestion to install Xubuntu afterwards. It installed showing no errors and I rebooted. No GUI. I tried all of the suggestions to start the GUI (i.e., startx, -reconfig xserver, etc.), but I get different errors depending on which one I try. Regardless, they all mean the same thing: that the directory doesn't exist.

It's a P3 with 896mb RAM, so it should be able to handle it. It has been running a WinXP server for months with no problems and still is, but I would like to switch. Any help is appreciated. Thanks in advance!

---

### Post by mlind on 2006-06-13
Hi,
do you have xubuntu-desktop package installed ?

in text terminal type
```

sudo aptitude install xubuntu-desktop

```

And please post your /etc/X11/Xorg.0.log so we can see what's wrong
with Xserver.

---

### Post by Indifferent on 2006-06-14
Yes, I was laoding Xubuntu from aptitude, because I read that it would load and unload all dependencies. It would give the error, that X11 did not exist, so apparently it was not loading all dependencies. I just used apt-get and it installed a booted just fine. AS a matter of fact, I'm posting from it now. :) Aptitude has worked fine for all other packages. One thing I did notice, that when I used aptitude to load Xubuntu and logged out after, the splash screen was always for Edubuntu. I tried this 4 times and everytime the same result until now using apt-get. Just a funky glitch I suppose.

Thanks for the fast reply and I appreciate the help!

---

