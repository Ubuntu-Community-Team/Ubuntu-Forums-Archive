---
title: "Firefox Hangs"
date: 2012-06-09
forum: Desktop Environments
---

### Post by piriton on 2012-06-09
I upgraded to Firefox 13 beta 1 on Ubuntu 12.04 and after 10 minutes of use, I cannot close any terminals or Firefox itself.  I also cannot access the Unity menu.

All I can do is to ssh in and kill the firefox process.

Is this a known issue ?

---

### Post by Frogs Hair on 2012-06-09
13 is a regular release and not beta unless had a PPA installed. I have not seen anything written about this. The Nightly build upgraded to 16 alpha today and is running well.

---

### Post by piriton on 2012-06-09
I dont think that I am using a PPA, how can I tell ?

I there an apt logfile so that I can check the source of where the RPM was installed from ?

```

cat /etc/apt/sources.list

deb http://fr.archive.ubuntu.com/ubuntu/ precise main restricted multiverse

deb http://fr.archive.ubuntu.com/ubuntu/ precise-updates main restricted multiverse

deb http://fr.archive.ubuntu.com/ubuntu/ precise universe
deb http://fr.archive.ubuntu.com/ubuntu/ precise-updates universe

deb http://fr.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted multiverse
deb http://security.ubuntu.com/ubuntu precise-security universe

deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main

```

---

### Post by vasa1 on 2012-06-10
[QUOTE=piriton;12013260]I dont think that I am using a PPA, how can I tell ?

I there an apt logfile so that I can check the source of where the RPM was installed from ?
...

No **rpm**s for Ubuntu as far as I know. Ubuntu, which is Debian-based, uses **deb**s.

Anyway, open the Update Manager GUI, then click on Settings in the bottom left, and then click on the tab called "Other Software". That will list any ppas you have.

By the way, are you the only user of your computer?

---

### Post by piriton on 2012-06-10
oops my  mistake

I there an apt logfile so that I can check the source of where the apt was installed from ?

Also where is the PPA configuration held, I would like to cat a file to check that out.

---

### Post by vasa1 on 2012-06-10
> **piriton said:**
> oops my  mistake

I there an apt logfile so that I can check the source of where the apt was installed from ?

Also where is the PPA configuration held, I would like to cat a file to check that out.

```
man apt-cache
```may help?

---

### Post by Frogs Hair on 2012-06-10
If you did not enter a repository manually for an Aurora or Nightly build the update came from the Ubuntu repository. If Firefox is affecting the whole desktop I would suggest re-installing the package. A corrupt profile should not affect other applications , but a corrupt installation could.

---

### Post by piriton on 2012-06-14
Both KDE and GNOME have this issue, whereby I cannot click on any windows to make them come into focus, so I am essentially locked out.

I also cannot ctrl-alt back to a console, and restart the desktop.

I have to power off :-(

---

