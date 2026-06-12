---
title: "Older Dell Support"
date: 2009-04-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by lost. on 2009-04-16
Is Dell (or anyone else) offering support for older Dells? I obtained an older Inspiron 4500S and everything works except for the video card. With help from another forum post, I figured out it was an 82845G/GL[Brookdale-G]/GE, but I can't seem to get much further. I tried to download the driver recommended in the forum post [http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=865&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go]("http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=865&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go") but I wasn't able to install it. It gave me the following errors and I'm not sure what it means.

```
Compiling new agpgart module...

ERROR: AGPGART module did not compile

Compiling DRM module...

ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.
```

---

### Post by coffeeaddict22 on 2009-04-18
Hi,
Seems there is a problem with the card, but you can get away with it- have a look at [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/278431]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/278431")
If you turn off desktop effects, you should be OK.

---

### Post by lost. on 2009-04-18
You seem to be right. I suppose I should be happy, seeing as the 8 year old dell I inherited otherwise works great! Thanks much.

- Walter

---

