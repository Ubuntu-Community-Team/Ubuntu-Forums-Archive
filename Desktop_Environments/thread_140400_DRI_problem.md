---
title: "DRI problem"
date: 2006-03-06
forum: Desktop Environments
---

### Post by none on 2006-03-06
**PLEASE DELETE** problem answered [http://ubuntuforums.org/showthread.php?t=119662&highlight=Radeon+Xpress+200M](http://ubuntuforums.org/showthread.php?t=119662&highlight=Radeon+Xpress+200M)

I have been trying to get X to start but i keep getting a dri. I have read all the post on getting dri working with an ati card none seem to work. The error i get is (EE) RADEON(0): [dri] DRIScreenInit failed. Disabling DRI. Would it be posible to boot x without dri or do i need it?


```

Section "Device"
      Identifier      "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
      Driver          "ati"
      BusID          " PCI:1:5:0"

```

```

Section "Module"
      Load "GLcore"
      Load "i2c"
      Load "bitmap"
      Load "ddc"
      Load "dri"
      Load "extmod"
      Load "freetype"
      Load "glx"
      Load "int10"
      Load "type1"
      Load "vbe"
EndSection

```


-none

---

