---
title: "Update broke Network Monitor/network-admin"
date: 2006-09-23
forum: Desktop Environments
---

### Post by KrakensDen on 2006-09-23
After using a Mac for a week, I was inspired to remove the requirement for authentication before changing network settings. So I fired up visudo, added the following line:
```

myusername localhost = /usr/bin/network-admin

```
and prepared for one less distraction. Unfortunately, network-admin now refuses to launch from the Network Monitor applet, and still requires authentication if you run it from the command line.

Any ideas as to the cause?

---

