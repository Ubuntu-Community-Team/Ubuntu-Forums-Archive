---
title: "Help getting a Gdk-WARNING **: Local not supported"
date: 2006-09-17
forum: Desktop Environments
---

### Post by Omnios on 2006-09-17
Hi I get this error when ever I try openning or doing stuff in termainal. 

```

 Gdk-WARNING **: locale not supported by C library

```

 I did some fancy lib upgrades to get an external program installed and have been getting this now. Though proably simple the error message did not lead me to a solution.

---

### Post by Anduu on 2006-09-18
> **Omnios said:**
> Hi I get this error when ever I try openning or doing stuff in termainal. 

```

 Gdk-WARNING **: locale not supported by C library

```

 I did some fancy lib upgrades....

There is your problem...try undoing what you did.

---

### Post by Omnios on 2006-09-19
Kewl got this warning from Aptitude.

 ```

perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_ALL to default locale: No such file or directory


```

 Seems to be a alnguage thing so the main language looks ok but have to figure out this LC_ALL = (unset),  Cannot set LC_ALL to default locale: No such file or directory. Now I have to see what happened to the LC_ALL file.

---

### Post by Omnios on 2006-10-04
K latest problem I am having. I tryed installing globs video benchmarks and got a pearl error where it would not launch.

```
tom@miko:~$ globs

(globs:8725): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Traceback (most recent call last):
  File "/usr/bin/globs", line 31, in ?
    locale.setlocale(locale.LC_ALL, '')
  File "/usr/lib/python2.4/locale.py", line 381, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting
tom@miko:~$

```


Alos with locals I got this.
```
tom@miko:~/tarball/globs-0.1$ sudo dpkg-reconfigure locales
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_ALL to default locale: No such file or directory
Generating locales...
  en_AU.UTF-8... up-to-date
  en_BW.UTF-8... up-to-date
  en_CA.UTF-8... up-to-date
  en_DK.UTF-8... up-to-date
  en_GB.UTF-8... up-to-date
  en_HK.UTF-8... up-to-date
  en_IE.UTF-8... up-to-date
  en_IN.UTF-8... up-to-date
  en_NZ.UTF-8... up-to-date
  en_PH.UTF-8... up-to-date
  en_SG.UTF-8... up-to-date
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... up-to-date
  en_ZW.UTF-8... up-to-date
Generation complete.
Current default timezone: 'US/Eastern'.
Local time is now:      Wed Oct  4 19:05:32 EDT 2006.
Universal Time is now:  Wed Oct  4 23:05:32 UTC 2006.
Run 'tzconfig' if you wish to change it.

```

 Any help on configing  LC_ALL = (unset) would be apreaciated.

---

