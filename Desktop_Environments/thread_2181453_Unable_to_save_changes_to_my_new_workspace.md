---
title: "Unable to save changes to my new workspace"
date: 2013-10-17
forum: Desktop Environments
---

### Post by cosname on 2013-10-17
I`ve reinstalled my Ubuntu 13.04 with Ubuntu 12.04
My PC is Dell inspiron 5520.

On fresh 12.04 x64 install i did:
an update
Installed some work apps (like sublime, komodo, filezilla, wine)
Installed Hybrid driver for Ati Radeon HD 7500/7600 series

The /home main user folder remains from 13.04.

And then i tried to configure:
- wallpaper
- change settings for touchpad (for exampe two finger scolling)
- rearange fast launch on unity launchbar
And all failed, not saves at all!

How i can solve this?
N.B.: Also CompizConfig Settings menager is not launching

```

cosname@cosname:~$ ccsm


(process:6877): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 94, in <module>
    import ccm
  File "/usr/lib/python2.7/dist-packages/ccm/__init__.py", line 1, in <module>
    from ccm.Conflicts import *
  File "/usr/lib/python2.7/dist-packages/ccm/Conflicts.py", line 26, in <module>
    from ccm.Constants import *
  File "/usr/lib/python2.7/dist-packages/ccm/Constants.py", line 85, in <module>
    locale.setlocale(locale.LC_ALL, "")
  File "/usr/lib/python2.7/locale.py", line 539, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting

```

However setings for new temporar user are saving... What should i reset/remove?

---

### Post by cosname on 2013-10-17
Solved!

I guess that downgrading the Ubuntu causes some problems with account. So i removed all unwanted files and configuration and reloged in. All now works good!

---

