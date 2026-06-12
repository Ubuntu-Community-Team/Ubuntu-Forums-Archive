---
title: "Cedega 5.1.3 Install problem"
date: 2006-06-10
forum: Gaming &amp; Leisure
---

### Post by Unknown on 2006-06-10
I downloaded the tar.gz file from the net and unzipped it. Copied the files i needed to copy to their Directories.

The next step is to start it for the first time. 
I do it like it says, not as root.

When i try starting cedega it just says that:

Traceback (most recent call last):
  File "/usr/lib/transgaming_cedega/Point2Play_gui.py", line 35, in ?
    raise Point2PlayError(_("Unable to load GTK2 Python bindings") + "(%s)" % str( sys.exc_info()[1] ) )
NameError: name '_' is not defined

Do someone now the problem and i dont mind a little help how to solve it :)

Im Running Ubuntu 6.06 Dapper Drake

---

### Post by FizDev on 2006-06-10
Stupid question : Did you compiled and installed it before?

You could always go download the .deb, way less trouble installing it. Just do :
```
sudo dpkg -i NameoftheDebPackage.deb
```

---

