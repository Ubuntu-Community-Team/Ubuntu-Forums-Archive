---
title: "Problem with Brightness"
date: 2013-06-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by piyushoo71 on 2013-06-06
I have dell 1558 studio and when I reduce the brightness , my screen hangs and looks like this image.. Please tell me solution for this problem.

---

### Post by Toz on 2013-06-06
Hello and welcome to the forums.

Which version of Ubuntu have you installed? Which kernel version are you using?

Have you tried any kernel boot paramaters? Depending on the installed kernel version, I would suggest trying the following:

_< 3.8_
```
acpi_backlight=vendor
```

_3.8 or greater_
```
acpi_osi=Linux acpi_backlight=vendor dell_laptop.backlight=0
```

More information about how to set/use kernel boot parameters can be found by clicking the "Kernel Boot Parameters" link in my signature.

---

### Post by piyushoo71 on 2013-06-07
I am using ubuntu 12.04.2

---

### Post by piyushoo71 on 2013-06-07
i was try this and this was not resolved my problem but i think it is a problem of graphics driver

---

