---
title: "ipodder install"
date: 2005-10-20
forum: Desktop Environments
---

### Post by shevek on 2005-10-20
Hello:
  I am trying to install ipodder podcasting client using Synaptic. This package has some dependencies (wxpython and some others) One of them is python-wxversion, and the installation of this package crashes. The error message is:
> dpkg: error al procesar /var/cache/apt/archives/python-wxversion_2.6.1.1.1ubuntu2_all.deb (--unpack):
 intentando sobreescribir `/usr/lib/python2.4/site-packages/wxversion.py', que está también en el paquete wxpython2.5.3
Se encontraron errores al procesar:
 /var/cache/apt/archives/python-wxversion_2.6.1.1.1ubuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Well it's in spanish, but the message says it is trying to overwrite wxversion.py, who is in wxpython2.5.3 as well. I think the problem is the last wxpython version in the repositories is 2.5.3, while this package version (at least the name) is 2.6.1.1. I have tried to force Synaptic to install an older version, but it seems this is the only version of that package. Ipodder is installed, and it seems to be usable, but it is impossible to install that package.

---

