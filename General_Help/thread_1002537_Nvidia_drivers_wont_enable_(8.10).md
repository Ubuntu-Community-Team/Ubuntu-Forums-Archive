---
title: "Nvidia drivers wont enable (8.10)"
date: 2008-12-05
forum: General Help
---

### Post by thefishki345 on 2008-12-05
Hi
there have been lots of other threads about this, and I have tried most solutions but none of them have worked.

After upgrading to 8.10 from 8.04 64 bit ver. I tried to enable restricted drivers for  my 8800gts 512 nvidia card but it  would do a downloading drivers for like 4 seconds with an undetermined % then disappears and it still says the driver is not activated.
Note- the graphics drivers worked fine on 8.04 though i'm not sure what version the old one was.

Please, any  solutions/ideas would be helpful.
thanks :D

---

### Post by DieB on 2008-12-05
try to install via synaptic (system-administration) - befor check which ersion is recommended.

---

### Post by thefishki345 on 2008-12-06
hi thanks for your reply.
Tried to install via synaptic before and now but got this error on most things (nvidia glx-driver new or w/e):
> nvidia-glx-new:

Package nvidia-glx-new has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list



177 is the recommended package

---

### Post by DieB on 2008-12-07
uninstall nvidai-glx-new. it is no longer in the intrepid - [see]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=nvidia-glx-new"), after that refresh the repositories, and mark the neded driver to be installed. hope that might get a help.

---

### Post by DieB on 2008-12-08
tryed that: [http://ubuntuforums.org/showthread.php?t=1004660](http://ubuntuforums.org/showthread.php?t=1004660)
?

---

