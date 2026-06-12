---
title: "Transparency suddenly off"
date: 2014-02-17
forum: Desktop Environments
---

### Post by cosmoflop12 on 2014-02-17
I am running Ubuntu 13.10. Immediately after installing the Nvidia 319 driver and rebooting, all transparency on my desktop (launcher, dock, conky) has gone away. It doesn't seemed to be turned off. Is there a way to fix or reset this? Thank you in advance, please tell me if any other information is required to fix this problem.

---

### Post by cosmoflop12 on 2014-02-17
Problem identified: The drivers have not been fully installed. How do I fix this?

---

### Post by cosmoflop12 on 2014-02-17
Also, I am receiving this error:

dpkg: error processing nvidia-319-updates (--configure):
 package nvidia-319-updates is not ready for configuration
 cannot configure (current status `half-installed')
Errors were encountered while processing:
 nvidia-319-updates
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by cosmoflop12 on 2014-02-18
Fixed with sudo apt-get install --reinstall nvidia-319-updates.

---

### Post by cosmoflop12 on 2014-02-18
Lame thread, sorry.

---

