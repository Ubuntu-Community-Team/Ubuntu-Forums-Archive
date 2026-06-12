---
title: "Removing amule-common"
date: 2006-09-06
forum: Desktop Environments
---

### Post by Jonathan Métillon on 2006-09-06
Hi,

After [failing to upgrade aMule 2.1.0 to 2.1.3](http://ubuntuforums.org/showthread.php?t=247277) because of a missing dependency (libcrypto++5.2c2) I've not been able to go back to 2.1.0.

Synaptics stops my update with this error: *E: amule-common: subprocess post-removal script returned error exit status 2*

Then *sudo apt-get remove amule-common* gives:

```

Removing amule-common ...
dpkg-divert: mismatch on package
  when removing `diversion of /usr/bin/ed2k by amule'
  found `diversion of /usr/bin/ed2k to /usr/bin/ed2k.xmule by amule-utils'
dpkg: error processing amule-common (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 amule-common
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

This error prevents me do to anything with packages. I can't install or remove anything. And I can't keep my computer up to date!

What should I do to force the removing of amule-common?

Thank you!

---

### Post by Jonathan Métillon on 2006-09-10
[Thanks to Thermoman]("http://forum.amule.org/thread.php?postid=59714#post59714") at aMule Project forums I've been able to fix this!

---

