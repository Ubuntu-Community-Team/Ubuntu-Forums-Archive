---
title: "update from site?"
date: 2006-08-16
forum: Desktop Environments
---

### Post by drtvasudevan on 2006-08-16
is there anyway to update ubuntu from the [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
i just cant do it from aptitude synaptic apt get etc.
:-s

---

### Post by ardchoille on 2006-08-16
> **drtvasudevan said:**
> is there anyway to update ubuntu from the [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
i just cant do it from aptitude synaptic apt get etc.
:-s

I use the following in my sources.list and updates are fast:

```

deb http://archive.ubuntu.com/ubuntu/ dapper main multiverse restricted universe
deb-src http://archive.ubuntu.com/ubuntu/ dapper main multiverse restricted universe
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main multiverse restricted universe
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main multiverse restricted universe
deb http://security.ubuntu.com/ubuntu/ dapper-security main multiverse restricted universe
deb-src http://security.ubuntu.com/ubuntu dapper-security main multiverse restricted universe
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main multiverse restricted universe
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main multiverse restricted universe

```

What is the apt-get command you are using for updates?

---

### Post by drtvasudevan on 2006-08-16
my list was fixed by automatix.
more or less the same.
ther eare issues i cant fatom.
it was updating normally some times after i fixed the network settings.
after the last update it is again malfunctioning.
i am tired of trying to fix it any more.
what i want to know is is there a method i can follow to update without depending on the synaptic, update manager, aptitude, aptget all of them have failed.

---

### Post by Rainmaker_mail on 2006-08-16
Hi,
Not sure if this can solve your problem but you can download the packages that you want from : [http://packages.ubuntu.com](http://packages.ubuntu.com) but there are lots of dependencies you have to be look out for and download.

I am also having the same problem but still have no luck to do automatic update. Am considering to download the repo manually. (see for instructions - [http://www.debian.org/doc/manuals/repository-howto/repository-howto)](http://www.debian.org/doc/manuals/repository-howto/repository-howto)).

You can also get the system to generate a clean sources.list for you (but does not help me in my problem). Url: [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

Best of luck.
RM

---

### Post by drtvasudevan on 2006-08-17
thanks for the inputs.
tried to download the updates compressed file but it wont download.
does it need the installer that are separate?
has anyone done update this way?

---

