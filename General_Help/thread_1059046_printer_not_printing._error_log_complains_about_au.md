---
title: "printer not printing. error log complains about authentication"
date: 2009-02-03
forum: General Help
---

### Post by bazzer on 2009-02-03
I can print a test page ok, but nothing else works. Found LOADS of these lines in the error log:
```
cupsdAuthorize: Local authentication certificate not found!
```
...but no help from any of the threads here or on cups.org.
I've tried uninstall, reinstall, use hplip, change the device uri to file:/dev/usb/lp0, symlink /etc/cups/certs to /var/run/cups/certs, create an openssl certificate.....

I'm at the very end of my tether so please - any ideas?

---

### Post by bazzer on 2009-02-04
Come on guys - this worked under Hardy, something must have changed in CUPS to break it?

---

### Post by bazzer on 2009-02-05
ok workaround found now. It isn't the authentication issue after all, the first message seems to be related to the cups web page.

The one that's causing issues in the log file is: ```
prnt/backend/hp.c 711: INFO: open print channel failed
```

Turns out that the driver for the p3005 is set to 1284.4, which causes the printer to appear to be disconnected. If you set it to raw mode it works. 
So, in /usr/share/hplip/data/models/models.dat under the [p3005] section change ```
io-mode=3
``` to ```
io-mode=1
```

From: [https://answers.launchpad.net/hplip/+question/41463]("https://answers.launchpad.net/hplip/+question/41463")

---

