---
title: "Locale Issues Will Not Allow Application Launching"
date: 2013-10-13
forum: Desktop Environments
---

### Post by yn2 on 2013-10-13
Hello,

Have a machine with Ubuntu 13.04 installed on it. No additional repos added. Has issues with Locale which have been problematic with perl but since i don't code in perl i ignored it until now. Trying to start bitcoind but getting a core dump.
The error is this:
```
user@machine:~/.bitcoin$ bitcoind
terminate called after throwing an instance of 'std::runtime_error'
  what():  locale::facet::_S_create_c_locale name not valid
Aborted (core dumped)
```

When tried an unknown command getting this error:
```
user@machine:~/.bitcoin$ what
Sorry, command-not-found has crashed! Please file a bug report at:
https://bugs.launchpad.net/command-not-found/+filebug
Please include the following information with the report:

command-not-found version: 0.3
Python version: 3.3.1 final 0
Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring
Exception information:

unsupported locale setting
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/CommandNotFound/util.py", line 24, in crash_guard
    callback()
  File "/usr/lib/command-not-found", line 69, in main
    enable_i18n()
  File "/usr/lib/command-not-found", line 40, in enable_i18n
    locale.setlocale(locale.LC_ALL, '')
  File "/usr/lib/python3.3/locale.py", line 541, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting

```
Any ideas on what to do?
My locale is US:
```
user@machine:~/.bitcoin$ cat /etc/default/locale
LANG="en_US.UTF-8"
```

Thanks

---

### Post by safir on 2013-10-29
I have the same problem. I upgraded from Ubuntu 13.04 AMD64 to Ubuntu 13.10 AMD64 saucy. Upgrade went well but then on login get the same message. I am using AMD 64 processor. When I use /etc/default/locale, it says I don't have permission. LANG="en_US.UTF-8" doesnot allow to change locale.
Sorry, command-not-found has crashed! Please file a bug report at:
[https://bugs.launchpad.net/command-not-found/+filebug](https://bugs.launchpad.net/command-not-found/+filebug)
Please include the following information with the report:

command-not-found version: 0.3
Python version: 3.3.2 final 0
Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy
Exception information:

unsupported locale setting
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/CommandNotFound/util.py", line 24, in crash_guard
    callback()
  File "/usr/lib/command-not-found", line 69, in main
    enable_i18n()
  File "/usr/lib/command-not-found", line 40, in enable_i18n
    locale.setlocale(locale.LC_ALL, '')
  File "/usr/lib/python3.3/locale.py", line 541, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting

---

