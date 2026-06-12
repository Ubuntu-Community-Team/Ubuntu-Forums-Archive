---
title: "Problem installing Thunderbird"
date: 2006-12-04
forum: Desktop Environments
---

### Post by Panzerknacker on 2006-12-04
Hello, firsttimer on Ubuntu and I have a question regarding Thunderbird. I get the following error when trying to re/install Thunderbird 1508.

(Reading database ... dpkg: error processing /var/cache/apt/archives/mozilla-thunderbird_1.5.0.8-0ubuntu0.6.10_i386.deb (--unpack):
 unable to open files list file for package `libgtkspell0': No such device or address

Does anyone know how to solve this?

Just found out that I can not install any package anymore.

---

### Post by renzokuken on 2006-12-04
not entirely sure it will help but have you enabled all repositories (universe and multiverse)?

```
sudo gedit /etc/apt/sources.list
```

(use "kedit" if your using KDE as opposed to gnome)

then make sure all the repos (the lines starting with "deb") have the # symbol removed from infront.

then try again

---

