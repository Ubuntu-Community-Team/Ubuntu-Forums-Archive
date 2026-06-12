---
title: "Gurb boot resolution"
date: 2009-04-25
forum: General Help
---

### Post by sadman64 on 2009-04-25
My boot resolution for my Ubuntu install is wrong.

This post tells me how to fix it, but it doesn't have the resolution I need.
[http://ubuntuforums.org/showthread.php?p=1505142](http://ubuntuforums.org/showthread.php?p=1505142)

This explains how to find the codes, but it still doesn't list the resolution I need.
[http://ubuntuforums.org/showpost.php?p=2071872&postcount=22](http://ubuntuforums.org/showpost.php?p=2071872&postcount=22)

sudo hwinfo --framebuffer | grep 'Mode '
Mode 0x0301: 640x480 (+640), 8 bits


The resolution I need is 1360x768, preferably 32bit colors.
Does anyone know the VGA code for that resolution?
Thank you.

---

### Post by sadman64 on 2009-04-25
any ideas?

---

### Post by dcstar on 2009-04-25
> **sadman64 said:**
> My boot resolution for my Ubuntu install is wrong.

This post tells me how to fix it, but it doesn't have the resolution I need.
[http://ubuntuforums.org/showthread.php?p=1505142](http://ubuntuforums.org/showthread.php?p=1505142)

This explains how to find the codes, but it still doesn't list the resolution I need.
[http://ubuntuforums.org/showpost.php?p=2071872&postcount=22](http://ubuntuforums.org/showpost.php?p=2071872&postcount=22)

sudo hwinfo --framebuffer | grep 'Mode '
Mode 0x0301: 640x480 (+640), 8 bits


The resolution I need is 1360x768, preferably 32bit colors.
Does anyone know the VGA code for that resolution?
Thank you.

There is only a certain amount of resolutions in the VGA standard, do not assume that the one you want is actually available.

---

### Post by sadman64 on 2009-04-25
> **dcstar said:**
> There is only a certain amount of resolutions in the VGA standard, do not assume that the one you want is actually available.

well, i'm just looking for one that will display (somewhat) right on a 1360x768 monitor

---

### Post by sadman64 on 2009-04-26
To be more specific, the problem I have is my login screen. The loading screen, etc., isn't important. I would think that it can be displayed in the correct resolution since the resolution is used once I log in.

---

