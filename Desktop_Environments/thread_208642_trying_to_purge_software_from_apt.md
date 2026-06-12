---
title: "trying to purge software from apt"
date: 2006-07-03
forum: Desktop Environments
---

### Post by koumdros on 2006-07-03
after having some problems when trying to install automatix i was told i need to "purge" an erroneus package from apt.

initally i got this error ```
 Setting up mozilla-firefox-locale-el (1.0-1ubuntu1) ... /var/lib/dpkg/info/mozilla-firefox-locale-el.postinst: line 11: update-mozilla-firefox-chrome: command not found dpkg: error processing mozilla-firefox-locale-el (--configure): subprocess post-installation script returned error exit status 127 Errors were encountered while processing: mozilla-firefox-locale-el E: Sub-process /usr/bin/dpkg returned an error code (1) 
```

and then when i tried to do this command

code] sudo aptitude purge mozilla-firefox-locale-el [/code]

i got something similar...

```

Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
The following packages are unused and will be REMOVED:
  mozilla-firefox-locale-el
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 733kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 61215 files and directories currently installed.)
Removing mozilla-firefox-locale-el ...
/var/lib/dpkg/info/mozilla-firefox-locale-el.postrm: line 12: update-mozilla-firefox-chrome: command not found
dpkg: error processing mozilla-firefox-locale-el (--purge):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 mozilla-firefox-locale-el
E: Sub-process /usr/bin/dpkg returned an error code (1)
Ack!  Something bad happened while installing packages.  Trying to recover:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done

```

so how do i purge this problematic package from apt... was i right in trying the afformentioned command?

---

### Post by evilghost on 2006-07-03
Try:

```
dpkg --purge remove mozilla-firefox-locale-el
```

---

