---
title: "OGMRIP Install Problems"
date: 2005-05-20
forum: Desktop Environments
---

### Post by Sniffer on 2005-05-20
My saga on 100% smooth Ubuntu Box continues... :) 

Ok i have installed mplayer from the source following this tutorial and everything works great:

[http://www.ubuntuforums.org/showthread.php?t=31061](http://www.ubuntuforums.org/showthread.php?t=31061)


Then i went to install from the source as well OGMRIP, i have faced some dependecies problems that i could solve with some packages but I'm stuck in here:

**Mplayer was not compiled with Xvid support and OGMRIP needs mplayer with Xvid support...**

So my questions:

Can i workaround this problem without uninstalling mplayer?

If i need to uninstall and compile mplayer again how can i add the Xvid support when compiling?

Thks, really needing this proggie.

Sniff.

---

### Post by Sniffer on 2005-05-20
Ok, just found:

** ./configure --with-xvidcore=/usr/local/lib/libxvidcore.a (if libxvidcore.a was installed in /usr/local/lib)**

---

