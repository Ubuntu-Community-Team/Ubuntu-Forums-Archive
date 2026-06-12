---
title: "wine Arabic Ubuntu 10.04"
date: 2012-04-05
forum: Egypt Team
---

### Post by hcj on 2012-04-05
hi eb

I'm running wine 1.2 on ubuntu 10.04
Arabic is not displayed properly
[IMG]http://www8.0zz0.com/2012/04/06/00/519854996.png[/IMG]

I copied all windows fonts to ~/.wine/drive_c/windows/fonts/
but it did not help !

Any help fixing this ?

following commands' output from my ubuntu box:

```
$ dpkg --get-selections wine*
wine1.2						install
wine1.2-gecko					install
winetricks					install
$ dpkg --get-selections ttf-ms*
ttf-mscorefonts-installer			install
$ uname -r
2.6.32-21-generic
$ wine --version
wine-1.2.3
$ cat /etc/apt/sources.list | egrep -v "^s*(#|$)"
deb http://eg.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://eg.archive.ubuntu.com/ubuntu/ lucid main restricted
deb http://eg.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://eg.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb http://eg.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://eg.archive.ubuntu.com/ubuntu/ lucid universe
deb http://eg.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://eg.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb http://eg.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://eg.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://eg.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://eg.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
deb http://archive.canonical.com/ lucid partner
deb http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu lucid main
```

---

### Post by thelinuxer on 2012-04-07
Please try to ask your question on [www.facebook.com.com/groups/ubuntueg](www.facebook.com.com/groups/ubuntueg)
It's more active there.

---

### Post by thelinuxer on 2012-04-07
Sorry [https://www.facebook.com/groups/ubuntueg](https://www.facebook.com/groups/ubuntueg)

---

### Post by heron92 on 2012-08-05
How can I make my Ubuntu 10.04 supports the Arabic language

Please help:(

---

