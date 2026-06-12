---
title: "Printing with PIXMA Series from Canon"
date: 2005-10-24
forum: Desktop Environments
---

### Post by toledo64fx on 2005-10-24
I don't know about you guys but i don't like the drivers for my IP3000 printer from Canon... why in Windows i get great printing and not in Ubuntu ??


What driver should i use ???

---

### Post by henrrrik on 2005-10-24
As far as I know the only linux driver that works is with the PIXMA series (or pretty much any inkjet) the TurboPrint package, but it will set you back about US $40.
[http://www.turboprint.de/english.html](http://www.turboprint.de/english.html)

You should tell Canon that you want linux drivers, they won't release any unless they know there's a demand.

---

### Post by Kinux on 2005-10-25
I too have a Canon Pixma printer, IP4000.

In " [ftp://download.canon.jp/pub/driver/bj/linux/](ftp://download.canon.jp/pub/driver/bj/linux/) " I found RPM based drivers for the IP4100 that is exactly the same as IP4000 sold in Japan.

There is also a 3100 that I think should be the same as 3000. Well, it works very well with my Fedora installation. I don't know yet how to use RPMs in Ubuntu.

Perhaps someone can take these and create a Ubuntu package.

---

### Post by KrisW on 2005-10-25
You can convert rpm files to deb by using the alien command.  First you must install the alien package.

But this isn't the cleanest way to handle things.

I work on an IP2000 printer, and use the linux BJC-7000 driver.  Works well, but not as good as the turboprint. (Turboprint prints the turboprint logo on every print, unless you pay for a license).

This BJC-7000 driver is known by ubuntu.

cheerz,

---

