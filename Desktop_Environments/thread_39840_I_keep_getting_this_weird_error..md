---
title: "I keep getting this weird error."
date: 2005-06-06
forum: Desktop Environments
---

### Post by MicroChris on 2005-06-06
Hey everyone, 

I keep getting this weird "error" while booting up, logging out, shutting down, installing/uninstalling, etc.

```
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
``` 

Anyone else getting this, and is it easy to fix?

Thanks,
Chris

---

### Post by Alexander Kirillov on 2005-06-06
[QUOTE=MicroChris]Hey everyone, 

I keep getting this weird "error" while booting up, logging out, shutting down, installing/uninstalling, etc.

```
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
``` 

Anyone else getting this, and is it easy to fix?

Thanks,
Chris[/QUOTE]
 What is the output of "locale" command?

---

### Post by MicroChris on 2005-06-06
```
chris@ubuntu:~$ locale
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=
``` 


Thanks, 
Chris

---

### Post by Alexander Kirillov on 2005-06-07
[QUOTE=MicroChris]```
chris@ubuntu:~$ locale
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=
``` 


Thanks, 
Chris[/QUOTE]
 Hmm... looks fine to me. Do you have "locales" and "localeconf" installed? Try 
sudo dpkg-reconfigure locales 
See also this page: [http://www.ubuntulinux.org/wiki/LocaleConf](http://www.ubuntulinux.org/wiki/LocaleConf)

---

### Post by MicroChris on 2005-06-08
Thanks Alexander.. Now I'm getting this:

```
Preconfiguring packages ...
/usr/bin/locale: Cannot set LC_CTYPE to default locale: No such file or directory
/usr/bin/locale: Cannot set LC_MESSAGES to default locale: No such file or directory
/usr/bin/locale: Cannot set LC_ALL to default locale: No such file or directory
localeconf.config: warning: could not find list of supported locales
Selecting previously deselected package locales.
(Reading database ... 73027 files and directories currently installed.)
Unpacking locales (from .../locales_2.3.2.ds1-20ubuntu13_all.deb) ...
Selecting previously deselected package localeconf.
Unpacking localeconf (from .../localeconf_0.9.4_all.deb) ...
Setting up locales (2.3.2.ds1-20ubuntu13) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_US:en_GB:en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Generating locales...
  en_US.UTF-8... done
Generation complete.

Setting up localeconf (0.9.4) ...
``` 

Still doing it. Hmmm.

Thanks a lot,
Chris

---

### Post by MicroChris on 2005-06-08
Nevermind. Seems to be gone now.

```
chris@ubuntu:~$ locale
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=
``` 

Thanks a lot everyone, especially Alexander!

-Chris

---

