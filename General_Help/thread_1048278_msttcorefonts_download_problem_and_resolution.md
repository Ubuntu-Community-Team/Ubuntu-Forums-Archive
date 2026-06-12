---
title: "msttcorefonts download problem and resolution"
date: 2009-01-23
forum: General Help
---

### Post by LightningCrash on 2009-01-23
.
Scenario:
--------------------------
-New 8.10 installation at work
-Proxy configured for this network segment
-Moved to an open network segment, disabled proxies
-Tried installing msttcorefonts
-Installation of msttcorefonts failed because it was still trying to go through the proxy and the proxy would not permit the download of .exe files. Wget was still picking up the environment variable "http_proxy" from god only knows where, I couldn't find it when I did an strace.

.
Solution:
--------------------------
Edited /etc/wgetrc
On Line 8: # use_proxy = on
Remove hash symbol, change on to off
Save file
Run `sudo apt-get install msttcorefonts` again, and you're all set.

---

