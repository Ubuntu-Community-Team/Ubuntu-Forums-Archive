---
title: "Steam problem"
date: 2014-03-22
forum: Gaming &amp; Leisure
---

### Post by Korkel on 2014-03-22
Hello,

When I want to open Steam I get an error:
[IMG]http://www.imgdumper.nl/uploads7/532dac19b5705/532dac19a9378-Schermafdruk_van_2014-03-22_16:28:10.png[/IMG]

---

### Post by efflandt on 2014-03-22
I take it you are running 64-bit 13.10. Steam is 32-bit and while 13.10 includes some 32-bit libs, apparently not all needed for games and graphics.

I needed to tell steam where some 32-bit libs were by creating **/etc/ld.so.conf.d/steam.conf** containing:```
/usr/lib32
/usr/lib/i386-linux-gnu/mesa
```and then running: **sudo ldconfig**

I also had to install **libglu1-mesa:i386** to resolve the missing libGL.so1 issue and **libxv1:i386** for a 32-bit graphic benchmark that complained about another missing lib.

My original [solved] post about that and launching steam source games with optirun (combo Intel/Nvidia graphics) is [http://ubuntuforums.org/showthread.php?t=2188201&p=12851705#post12851705](http://ubuntuforums.org/showthread.php?t=2188201&p=12851705#post12851705)

---

### Post by Korkel on 2014-03-22
OK, now I don't understand it...

---

### Post by thevypr on 2014-04-07
Install the corresponding libraries through apt, that always solves the problem for me.

---

