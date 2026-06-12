---
title: "External monitor is not detected in Ubuntu 12.04"
date: 2014-05-24
forum: Desktop Environments
---

### Post by Mekhron on 2014-05-24
I've been trying to extend my DELL S2340L monitor to my Lenovo y510p laptop. It clones the display fine but does not extend it, it cannot detect it. Nvidia X server settings is also not what other people have. 
What is the problem and how can I fix it? Thank you.

```
lspci | grep VGA 
//Output:
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)

01:00.0 VGA compatible controller: NVIDIA Corporation GK107M [GeForce GT 750M] (rev a1)
```
[IMG]http://s21.postimg.org/425rrk8hz/Screenshot_from_2014_05_24_14_28_43.png[/IMG]


[IMG]http://s3.postimg.org/p0otrp9lf/Screenshot_from_2014_05_24_14_30_39.png[/IMG]
[IMG]http://s30.postimg.org/az8fqgqnl/Screenshot_from_2014_05_24_14_35_37.png[/IMG]

---

### Post by Mekhron on 2014-05-24
[COLOR=#333333][FONT=UbuntuRegular]After I've tried everything, the solution was to upgrade to a newer version of Ubuntu.


[/FONT][/COLOR]

---

