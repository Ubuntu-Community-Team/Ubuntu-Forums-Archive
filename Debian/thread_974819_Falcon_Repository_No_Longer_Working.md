---
title: "Falcon Repository No Longer Working"
date: 2008-11-07
forum: Debian
---

### Post by dfreer on 2008-11-07
Running an up-to-date Debian Lenny 64-bit with a custom compiled kernel, been running a falcon repository on my server for about 2 years. I haven't added any new packages to it for just shy of a year, went to add some new packages and got this error message:
```
 === ERROR! ===

An error occured in falcon. This is probably a bug in the software.
Please file a bug at https://launchpad.net/falcon/+filebug and
include the following backtrace:

Traceback (most recent call last):
  File "/usr/bin/falcon", line 14, in ?
    import falcon
  File "/usr/lib/python2.4/site-packages/falcon/__init__.py", line 45, in ?
    import falcon.config
  File "/usr/lib/python2.4/site-packages/falcon/config.py", line 62, in ?
    class ConfigurationKey(models.Model):
  File "/usr/lib/python2.4/site-packages/falcon/config.py", line 64, in ConfigurationKey
    key = models.CharField(maxlength=50, unique=True)
TypeError: __init__() got an unexpected keyword argument 'maxlength'
```

Reported it as a bug on launchpad, haven't heard anything back:
[https://bugs.launchpad.net/falcon/+bug/290988](https://bugs.launchpad.net/falcon/+bug/290988)

Since then, I've been pulling my hair out trying to figure this out. I've tried installing several different versions of falcon, python-django, and have been experiencing crashes everytime. 

Can anybody help me with this, or suggest any better way of maintaining a repository? Most of the documents I've seen are concerned with building the packages themselves from source tarballs, whereas I already have all of the .deb's created, just need to update the Packages.gz files and such with the new packages.

---

