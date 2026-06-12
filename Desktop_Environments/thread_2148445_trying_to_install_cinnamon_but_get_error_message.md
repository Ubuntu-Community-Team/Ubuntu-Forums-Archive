---
title: "trying to install cinnamon but get error message"
date: 2013-05-25
forum: Desktop Environments
---

### Post by oren tal on 2013-05-25
Hi I am trying to install cinnamon but get the following error message:

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 cinnamon : Depends: gir1.2-muffin-3.0 but it is not going to be installed
            Depends: libmuffin0 but it is not going to be installed
            Recommends: nemo but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```
my OS is ubuntu 12.04.


How can I fix that?

---

### Post by kurt18947 on 2013-05-25
You could try installing Synaptic from the repositories if you don't have it.  Synaptic is able to resolve broken package problems and you can probably install Cinnamon from there as well.

---

### Post by converted on 2013-05-25
How are you trying to install it?

1.8 via PPA on 13.04 worked fine for me as described here.

[http://www.ubuntugeek.com/how-to-install-cinnamon-1-8-on-ubuntu-13-04.html](http://www.ubuntugeek.com/how-to-install-cinnamon-1-8-on-ubuntu-13-04.html)

I think that you have to be sure to specify nemo, but not sure if that's responsible for all your dependency issues.

---

