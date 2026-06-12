---
title: "error in apt-get"
date: 2006-07-09
forum: Desktop Environments
---

### Post by jsvidyad on 2006-07-09
Hi!!!

    As I was trying to install packages, I got an error. I tried to fix broken packages, and also tried to forcibly remove the package. No luck. The error message while trying to remove it was:
/var/lib/dpkg/info/xfingerd.postrm: line 5: /etc/init.d/inetd: No such file or directory
dpkg: error processing xfingerd (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 xfingerd
E: Sub-process /usr/bin/dpkg returned an error code (1)


The error message while trying to install it was practically similar with almost identical lines. I desperatley need help.

---

### Post by FredB on 2006-07-09
try this - but don't have big hope on it :

```
dpkg --configure -a
```

Maybe it will repair the error.

---

### Post by jsvidyad on 2006-07-09
Whew!! managed to fix it. just wanted lo let who ever is concerned that xfingerd depends on xinetd, but when we install xfingerd, xinetd does not get installed.

---

