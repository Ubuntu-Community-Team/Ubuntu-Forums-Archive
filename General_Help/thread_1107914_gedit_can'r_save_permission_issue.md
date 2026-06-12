---
title: "gedit can'r save/ permission issue"
date: 2009-03-27
forum: General Help
---

### Post by notoriousmic24 on 2009-03-27
While trying to disable the annoying system beep, I was trying to save the blacklist and this error comes up:

You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

This has never been a problem before. Any ideas?

---

### Post by VCoolio on 2009-03-27
If the file is in your root section you need to run gedit as root. In terminal or ALT+F2 run
```
gksudo gedit /path/to/file
```

---

