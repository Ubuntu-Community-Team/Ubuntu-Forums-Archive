---
title: "Help with Xen"
date: 2008-03-24
forum: Desktop Environments
---

### Post by d_xtremw on 2008-03-24
So ive been running xen trying to experiment with some stuff. but unfortunately ive run into an error i cant seem to get around. i keep getting this error

ERROR: Could not obtain handle on privileged command interface (13 = Permission denied)
error: Unable to open /usr/lib/rpm/rpmrc for reading: No such file or directory.
Valid, writable configuration found, using /home/server2/.xenman/xenman.conf
Traceback (most recent call last):
  File "/usr/share/xenman/src/xenman.py", line 1770, in <module>
    username = client_config.getHostProperty(prop_login, host)
  File "/usr/share/xenman/src/utils.py", line 232, in getHostProperty
    if not retVal.strip():
AttributeError: 'NoneType' object has no attribute 'strip'

does anyone know what this means or can they figure out a way to help??

---

