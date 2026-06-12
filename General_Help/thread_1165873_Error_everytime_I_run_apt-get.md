---
title: "Error everytime I run apt-get"
date: 2009-05-21
forum: General Help
---

### Post by vizitorq on 2009-05-21
```

Errors were encountered while processing:
 python-setuptools
 pitivi
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

not sure what I did to make this start happening but now I can't get updates or install anything new. At least not the things I've tried... SO, I have no idea what this means or what to do. Can I get a little help?

I use ubuntu hardy.

---

### Post by colau on 2009-05-21
> **vizitorq said:**
> ```

Errors were encountered while processing:
 python-setuptools
 pitivi
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

not sure what I did to make this start happening but now I can't get updates or install anything new. At least not the things I've tried... SO, I have no idea what this means or what to do. Can I get a little help?

I use ubuntu hardy.
```

dpkg --configure -a
apt-get update

```
Does it work?

---

### Post by vizitorq on 2009-05-21
```

kumi@throne:~ % sudo dpkg --configure -a
Setting up python-setuptools (0.6c8-0ubuntu2) ...
pycentral: pycentral pkginstall: not overwriting local files
pycentral pkginstall: not overwriting local files
dpkg: error processing python-setuptools (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of pitivi:
 pitivi depends on python-setuptools; however:
  Package python-setuptools is not configured yet.
dpkg: error processing pitivi (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-setuptools
 pitivi

```

i hope you know what that means. cuz I sure don't.

---

### Post by Yellow Pasque on 2009-05-21
[https://bugs.launchpad.net/ubuntu/+source/gdebi/+bug/204524](https://bugs.launchpad.net/ubuntu/+source/gdebi/+bug/204524)

---

### Post by ad_267 on 2009-05-21
Try:
```
sudo apt-get purge python-setuptools
sudo apt-get update
sudo apt-get install python-setuptools
sudo dpkg --configure -a
```

Edit: Probably try the workaround posted in that bug report first.

---

