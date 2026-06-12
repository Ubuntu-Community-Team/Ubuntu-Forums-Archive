---
title: "Cannot open CCSM - help"
date: 2011-06-26
forum: Desktop Environments
---

### Post by shottie on 2011-06-26
This is what i get when i try to run it from terminal:

```

(process:3071): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 93, in <module>
    import ccm
  File "/usr/lib/python2.7/dist-packages/ccm/__init__.py", line 1, in <module>
    from ccm.Conflicts import *
  File "/usr/lib/python2.7/dist-packages/ccm/Conflicts.py", line 26, in <module>
    from ccm.Constants import *
  File "/usr/lib/python2.7/dist-packages/ccm/Constants.py", line 79, in <module>
    locale.setlocale(locale.LC_ALL, "")
  File "/usr/lib/python2.7/locale.py", line 531, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting


```

Yesterday it was working fine. If i run 'locale' from terminal i get this:

```

locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=en_GB
LANGUAGE=en_GB:en
LC_CTYPE="en_GB"
LC_NUMERIC="en_GB"
LC_TIME="en_GB"
LC_COLLATE="en_GB"
LC_MONETARY="en_GB"
LC_MESSAGES=en_GB.UTF-8
LC_PAPER="en_GB"
LC_NAME="en_GB"
LC_ADDRESS="en_GB"
LC_TELEPHONE="en_GB"
LC_MEASUREMENT="en_GB"
LC_IDENTIFICATION="en_GB"
LC_ALL=


```

I am running 11.04 x64..
Any help much appreciated. Thanks!

---

### Post by shottie on 2011-06-26
Ok thanks to everyone who helped.. =;


I managed to find the problem myself.




I simply put this into the terminal:
```
export LC_ALL="C"

```
Then:
```
sudo dpkg-reconfigure --force locales
```

---

