---
title: "Unable to get Compix working with MSI Wind"
date: 2009-04-18
forum: Desktop Environments
---

### Post by homemadejam on 2009-04-18
Hey,
I have been trying for a while to get Compiz working on my MSI Wind U90x.
I have downloaded a script called compiz-check, and this is the info that it gives me:

```
Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect maximum 3D texture size
```

I have read somewhere that people have changed their color depth to 16 bits, and that seem to have worked for them. No luck for me though :(

I have checked on the MSI Wind forums, but it mentions nothing about compiz or 3D acceleration...

I have tried adding the following parts (found in the link below) to my xorg.conf: [http://wiki.msiwind.net/index.php/Gentoo#3D_Acceleration](http://wiki.msiwind.net/index.php/Gentoo#3D_Acceleration) But still no luck :/

It may be something really simple.. and knowing my luck it is.
Thanks in advice!

Jam

---

### Post by homemadejam on 2009-04-19
Bump...
Anyone got any ideas on this?

Thanks,
Jam

---

### Post by homemadejam on 2009-04-19
So no one has any ideas then?
I have tried everything I can think of :(


Jam

---

