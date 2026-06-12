---
title: "Python and NI GPIB-USB-HS 14.04"
date: 2016-05-11
forum: Education &amp; Science
---

### Post by etortorici on 2016-05-11
Hello,

I would like to be able to communicate with my lab equipment via NI's GPIB-USB-HS. I installed linux-gpib with the help from the following link
[HTML]http://linux-gpib-general.narkive.com/76BKTHLC/libgpib-so-0-not-found-on-debian[/HTML]
and
[HTML]http://ubuntuforums.org/showthread.php?t=2270802[/HTML]

from my experience with working on debian systems (run on raspberry pi's) that were set up by someone other than myself, the python code would open a serialport based on an address in /dev. However, when I type

```
ls /dev
```

with or without the GPIB-USB-HS plugged into my laptop, I get the same list, meaning that it is not showing up. When I type:

```
lsusb
```
this is returned:
```
Bus 001 Device 007: ID 3923:709b National Instruments Corp. GPIB-USB-HS
```

Thanks in advance.

---

