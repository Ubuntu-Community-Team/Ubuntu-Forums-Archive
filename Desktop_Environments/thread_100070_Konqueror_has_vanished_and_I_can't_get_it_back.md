---
title: "Konqueror has vanished and I can't get it back"
date: 2005-12-06
forum: Desktop Environments
---

### Post by essendon on 2005-12-06
Hi there.

I upgraded for 5.04 to 5.10 and konqueror is gone.  I tried getting it back using the synaptic package manager, but I get this error:

konqueror:
 Depends: kdebase-kio-plugins but it is not going to be installed


Then I tried to install the kdebase-kio-plugins and I get this:

kdebase-kio-plugins:
 Depends: dbus-1 but it is not going to be installed
 Depends: dbus-qt-1 but it is not going to be installed
 Depends: libhal-storage0 but it is not going to be installed
 Depends: libhal0 but it is not going to be installed

I tried installing the dbus-1 package and it caused all sorts of problems, so I took it off.  Can anyone help here?

---

### Post by aysiu on 2005-12-06
Maybe you have conflicted repositories? Can you post the output of this command? ```
cat /etc/apt/sources.list
```

---

### Post by essendon on 2005-12-07
here is the output:
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe main restricted
# deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

---

### Post by aysiu on 2005-12-07
You say you upgraded, but almost all of your repositories are Hoary ones (not Breezy). Follow the instructions in the first link in my sig. Don't worry--the first step backs up your sources.list.

---

