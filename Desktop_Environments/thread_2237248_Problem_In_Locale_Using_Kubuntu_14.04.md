---
title: "Problem In Locale Using Kubuntu 14.04"
date: 2014-07-31
forum: Desktop Environments
---

### Post by OssamaNas on 2014-07-31
When setting the country in locale to Syria (where we speak Arabic) and the language of the system is English the generated setlocal.sh script is :
```
export LANG=en_SY.UTF-8
export LANGUAGE=en
export LC_NUMERIC=en_SY.UTF-8
export LC_TIME=en_SY.UTF-8
export LC_MONETARY=en_SY.UTF-8
export LC_PAPER=en_SY.UTF-8
export LC_IDENTIFICATION=en_SY.UTF-8
export LC_NAME=en_SY.UTF-8
export LC_ADDRESS=en_SY.UTF-8
export LC_TELEPHONE=en_SY.UTF-8
export LC_MEASUREMENT=en_SY.UTF-8

```
While the correct locale should be:
```
export LANG="en_US.UTF-8"
export LANGUAGE=en
export LC_NUMERIC="ar_SY.UTF-8"
export LC_TIME="ar_SY.UTF-8"
export LC_MONETARY="ar_SY.UTF-8"
export LC_PAPER="ar_SY.UTF-8"
export LC_NAME="ar_SY.UTF-8"
export LC_ADDRESS="ar_SY.UTF-8"
export LC_TELEPHONE="ar_SY.UTF-8"
export LC_MEASUREMENT="ar_SY.UTF-8"
export LC_IDENTIFICATION="ar_SY.UTF-8"

```
So I changed manually in order to allow the programs to work correctly.
Also the default in /etc/defaults/local are correct :
```
LANG="en_US.UTF-8"
LC_NUMERIC="ar_SY.UTF-8"
LC_TIME="ar_SY.UTF-8"
LC_MONETARY="ar_SY.UTF-8"
LC_PAPER="ar_SY.UTF-8"
LC_NAME="ar_SY.UTF-8"
LC_ADDRESS="ar_SY.UTF-8"
LC_TELEPHONE="ar_SY.UTF-8"
LC_MEASUREMENT="ar_SY.UTF-8"
LC_IDENTIFICATION="ar_SY.UTF-8"

```
Is it just me or someone else is having this problem ?
Note: problem didn't exist when using Debian Wheezy with KDE desktop.

---

### Post by Rog131 on 2014-08-01
'Known' bugs: Changing country leads to invalid locale - [https://bugs.launchpad.net/ubuntu/+source/kde-runtime/+bug/1322968](https://bugs.launchpad.net/ubuntu/+source/kde-runtime/+bug/1322968)

---

