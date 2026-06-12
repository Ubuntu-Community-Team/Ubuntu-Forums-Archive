---
title: "Problem with locales"
date: 2007-03-10
forum: Desktop Environments
---

### Post by pablowwl on 2007-03-10
Hi! I'm new on this forum. And i have problem with language support.
First I've installed firefox 2 and my X won't run. I get message:

```
Kod:
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "(unset)",
        LC_ALL = (unset),
        LANG = "pl_PL"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "(unset)",
        LC_ALL = (unset),
        LANG = "pl_PL"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "(unset)",
        LC_ALL = (unset),
        LANG = "pl_PL"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C"). so i used command
```

So I used command:

```
dpkg-reconfigure xserver-xorg
```

Everything works fine but a few applications won't run (cedega, vlc etc.)
When I try to run one of this applications i get message (here cedega):

```
(Point2Play_gui.py:6061): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Traceback (most recent call last):
  File "/usr/lib/transgaming_cedega/Point2Play_gui.py", line 44, in ?
    locale.setlocale(locale.LC_ALL, '')
  File "/usr/lib/python2.4/locale.py", line 381, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting

```

I hope someone will help me.. Thanks :)

Ps Sorry for my English ;)

---

