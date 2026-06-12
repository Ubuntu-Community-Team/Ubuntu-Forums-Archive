---
title: "problem installing msttcorefonts"
date: 2009-03-05
forum: Desktop Environments
---

### Post by kestrel1 on 2009-03-05
I have just done a fresh install of Ubuntu 8.10 & getting things sorted. I thought I would install the Ubuntu-Restricted-Extras of which msttcorefonts is part, but I keep getting this error:
> All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

The above is actually from trying to install the fonts via apt-get after failure in synaptic.
I have tried removing with --purge, but I still get the same error when trying to install. Any ideas?

---

### Post by kestrel1 on 2009-03-09
Problem solved. See this thread: [http://ubuntuforums.org/showthread.php?t=1088515](http://ubuntuforums.org/showthread.php?t=1088515)

---

