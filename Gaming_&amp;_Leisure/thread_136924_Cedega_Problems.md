---
title: "Cedega Problems"
date: 2006-02-26
forum: Gaming &amp; Leisure
---

### Post by OtubrabNad on 2006-02-26
When ever I try to run a program through Cedega 5.0.3 in the command line, I get:
```
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
```
I then imput: LANG=en_US cedega [program name]
But this gives me:
```
(Point2Play_gui.py:11560): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Traceback (most recent call last):
  File "/usr/lib/transgaming_cedega/Point2Play_gui.py", line 40, in ?
    locale.setlocale(locale.LC_ALL, '')
  File "/usr/lib/transgaming_cedega/lib/python2.3/locale.py", line 381, in setlocale
    return _setlocale(category, locale)
locale.Error: locale setting not supported
```

 Does anyone have any idea what to do? I can't get tech support anymore from Transgameing because my subscription expired. Thanks.

---

### Post by OtubrabNad on 2006-03-16
bump

---

### Post by FizDev on 2006-03-16
I believe it is because you haven't installed a Cedega Engine... I think so, though I cannot verify right now. To install the Cedega Engine, I think you must do an update (it's somewhere in Cedega's menu), local or something. I'm not sure though...

---

### Post by tallganglyguy on 2006-05-18
Has this problem been resolved, and if so, how? I have the engine installed. You can't get that error without the engine installed. That is an error firing up the cedega version of Wine, that is only available after an engine is installed. Does anybody have any ideas?
-Jerry.

---

### Post by ChiaGod on 2006-05-26
I'm experiencing the same issue.  However I had a prior working Cedega (with engine and all installed).  Though my issue was caused by a bizarre chain of screw ups (on my part) resulting in a partially upgraded system (running Mandriva Cooker and now have half of the packages upgraded from 2006.1 to 2007)  anyway I found the thread below:

[http://www.linuxquestions.org/questions/showthread.php?t=407835](http://www.linuxquestions.org/questions/showthread.php?t=407835)

locale is a setting on the system and I'm not sure if its complaining mereley of the setting or the lack of the locale package.  (To get a glimpse of your settings you can type "locale" without the quotes in a console).  Anyway i'm instaling the locale package (along with 71 dependencies) on my machine and will post if that fixed the issue or not.

---

### Post by tallganglyguy on 2006-06-05
I was wondering if you had been able to make it work... Thanks.

---

