---
title: "Can't apply any visual effects"
date: 2010-06-15
forum: Desktop Environments
---

### Post by mrcool1990 on 2010-06-15
So everytime i try to apply any visual effect (System > Appearance > Visual effects) i choose any of Normal or Extra,an error occurs:

 > Desktop effects could not be enabled

My laptop is Asus G1S
Latest Nvidia driver is installed (195.xx)
OS: Ubuntu 10.4

Any help would be appreciated.

---

### Post by 3Miro on 2010-06-15
Go to System -> Admin -> Hardware Drivers to double-check that the latest driver is indeed available.

Then go to terminal (Apps -> Accessories -> Terminal) and type:
```
compiz --replace
```

This should give you a more comprehensive error code, "Desktop effects could not be enabled" is too generic.

---

