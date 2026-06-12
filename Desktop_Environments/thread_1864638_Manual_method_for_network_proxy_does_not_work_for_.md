---
title: "Manual method for network proxy does not work for Chrome on Ubuntu 11.10"
date: 2011-10-19
forum: Desktop Environments
---

### Post by JavaPenguin on 2011-10-19
The manual method for network proxy does not work for Chrome 14.0.835.202 on Ubuntu 11.10.
Automatic method discovers my proxy server and then it works fine. But if I set the same proxy settings manualy it does not works. Chromium has the same problem.
Firefox works fine.

Also works fine with Chrome 14.0.835.202 on Ubuntu 10.10., but not 11.10.

---

### Post by appier on 2011-11-29
Same issue from here as well.

---

### Post by efball3 on 2011-12-01
I start chrome this way:

/usr/bin/env SOCKS_SERVER="localhost:55580" no_proxy="localhost,127.0.0.1,XXXXX.com" /usr/bin/google-chrome

I dumped gnome/unity and went back to fvwm and this was the only way to get proxies working again.

---

