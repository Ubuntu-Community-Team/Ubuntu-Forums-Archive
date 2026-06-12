---
title: "can't remove ume-config-belmont"
date: 2009-03-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by carleton on 2009-03-03
Whenever I run upgrade on my dell mini 9, which tells me it will remove ume-config-belmont it come back with the follow error
[PHP]
Removing ume-config-belmont ...
Removing `diversion of /etc/X11/xorg.conf to /etc/X11/xorg.conf.orig by ume-config-belmont'
dpkg-divert: rename involves overwriting `/etc/X11/xorg.conf' with
  different file `/etc/X11/xorg.conf.orig', not allowed
dpkg: error processing ume-config-belmont (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 ume-config-belmont
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/PHP]

I think it might be messing up with my other installs and upgrades. Any help on trying to get this acually uinstalled would be great

cheers

---

### Post by carleton on 2009-03-03
Well, I didn't succeed in removing it, I ended up reinstall it after running sudo synaptic, which fixed it from being an broken package and I can now install other things (yay!) 

I think it came from trying to remove maximus, but I'm just leaving it there now rather then messing around with it

---

