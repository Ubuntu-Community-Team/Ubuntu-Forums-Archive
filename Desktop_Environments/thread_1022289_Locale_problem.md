---
title: "Locale problem"
date: 2008-12-26
forum: Desktop Environments
---

### Post by refdoc on 2008-12-26
I am running ubuntu 8.10 in en_UK locale.

Some applications I like running in different languages - and some applications i am busy translating applications in.

There appears to be a sudden problem with locale switch:

If I do export LC_ALL=locale_COUNTRY; whatever_gnome_command, I would normally expect that the programme will start up in the new locale - it does not since a couple of days. 

And running from the commandline  locale after setting things to ar_EG as an example  gives following result:

refdoc@refodc-laptop:~$ locale
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=en_GB.UTF-8
LC_CTYPE="ar_EG"
LC_NUMERIC="ar_EG"
LC_TIME="ar_EG"
LC_COLLATE="ar_EG"
LC_MONETARY="ar_EG"
LC_MESSAGES="ar_EG"
LC_PAPER="ar_EG"
LC_NAME="ar_EG"
LC_ADDRESS="ar_EG"
LC_TELEPHONE="ar_EG"
LC_MEASUREMENT="ar_EG"
LC_IDENTIFICATION="ar_EG"
LC_ALL=ar_EG
refdoc@refdoc-laptop:~$ 

A bug? something wrong with my setup? A friend has right now the very same problem

Anyone clever ideas

---

### Post by kforum on 2009-06-18
simply:
LC_CTYPE="ar_EG" != LC_CTYPE="ar_EG.UTF-8"

---

