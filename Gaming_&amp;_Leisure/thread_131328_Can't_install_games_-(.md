---
title: "Can't install games :-("
date: 2006-02-16
forum: Gaming &amp; Leisure
---

### Post by Dinchamion on 2006-02-16
Hello all,

I have a problem. I'm using 5.10 with Cedega, and any time I want to install a game (actually, starting the install), I have the following:

> (Point2Play_gui.py:11652): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Traceback (most recent call last):
  File "/usr/lib/transgaming_cedega/Point2Play_gui.py", line 40, in ?
    locale.setlocale(locale.LC_ALL, '')
  File "/usr/lib/transgaming_cedega/lib/python2.3/locale.py", line 381, in setlocale
    return _setlocale(category, locale)
locale.Error: locale setting not supported

Or:

> Warning: Language 'en_HU' was not found, retrying without country name...
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US

And when I try to set LANG to en_US, it does nothing.

I'm sorry if the above is confusing or missing some information, I'm relatively new to Ubuntu. However, I haven't had this problem on Mandrake or Suse, but I like Ubuntu very much, and hope there is some way to fix this.

I also tried 'dpkg-reconfigure locales', but whatever I set there, the same problem appears.

Please help!

---

### Post by Dinchamion on 2006-02-16
A little errata: it seems that GTA:SA starts the install properly (although I get the error messages as well), also DX:IW, so the above problem is with Heroes IV. (These three I tried so far)

---

