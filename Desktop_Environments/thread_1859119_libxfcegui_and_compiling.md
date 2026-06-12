---
title: "libxfcegui and compiling"
date: 2011-10-13
forum: Desktop Environments
---

### Post by Mark_in_Hollywood on 2011-10-13
From:

[http://goodies.xfce.org/projects/panel-plugins/xfce4-timer-plugin](http://goodies.xfce.org/projects/panel-plugins/xfce4-timer-plugin)

I d/l'd the 

xfce4-timer-plugin-0.6.2.tar.bz2

and extracted it into ~/XFCE-stuff folder. Then, in a Terminal I typed:

./configure

lots of output and all seemed OK, until:

checking for libxfcegui4-1.0 >= 4.2.0... not found
*** The required package libxfcegui4-1.0 was not found on your system.
*** Please install libxfcegui4-1.0 (atleast version 4.2.0) or adjust
*** the PKG_CONFIG_PATH environment variable if you
*** installed the package in a nonstandard prefix so that
*** pkg-config is able to find it.

SO, I hunt and peck for the missing libxfcegui4 in and around the internet, but to no avail. Can someone tell me how to get a timer applet installed and running in XFCE?

---

### Post by crdlb on 2011-10-13
There is an xfce4-timer-plugin package in 11.04. ```
sudo apt-get install xfce4-timer-plugin
``` That said, the compile is failing because you don't have the development headers package for libxfcegui4. So if you really did need to compile it, you could install libxfcegui4-dev, or use ```
sudo apt-get build-dep xfce4-timer-plugin
``` (which installs anything listed as a build dependency on the ubuntu package)

---

