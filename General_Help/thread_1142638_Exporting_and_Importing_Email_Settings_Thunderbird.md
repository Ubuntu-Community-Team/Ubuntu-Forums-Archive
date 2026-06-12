---
title: "Exporting and Importing Email Settings Thunderbird"
date: 2009-04-29
forum: General Help
---

### Post by Nano_ext3 on 2009-04-29
I was under the impression that if I save my .thunderbird folder before reformatting, that I could copy that folder back to 9.04 and load thunderbird and my accounts would be there.  This doesn't seem to be working, so I ask , how do I export/import accounts from file (.thunderbird)???  Or what do I have to do, I have the same folder on my desktop to re-copy from if necessary.

HALP

Thanks,

_Nano

---

### Post by maciu on 2009-04-29
edit the *profiles.ini* with the name of your old profile, so that thunderbird starts with it.

---

### Post by Nano_ext3 on 2009-04-29
```
[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
Path=w0ukh06q.default
```

That is my profile .ini, which is identical on each machine after copying it over from my desktop, I still dont understand how to get thunderbird to realize there's settings there

---

