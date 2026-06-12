---
title: "Install R in different directory with all dependencies"
date: 2013-02-14
forum: Education &amp; Science
---

### Post by megamonk on 2013-02-14
Hi,

can anyone please guide me on how to install R on a different directory with all dependencies?

```

apt-get install r-base

```wont do in my case at it installs it in my root. i need it to be installed in a different root directory.

tried using dpkg with the -instdir option but it doesnt resolve dependencies.

thanks

---

### Post by schragge on 2013-02-14
Try this
```

sudo apt-get clean
sudo apt-get -d --reinstall install r-base `apt-cache --recurse -i depends r-base|awk '/Depends: /{gsub(/^<|>$/,"",$2);print$2}'|sort -u`

```
The first command essentially *rm /var/cache/apt/archives/**. The second one recursively downloads *r-base* and all its dependencies into */var/cache/apt/archives/*, but stops short of (re)installing them.

After that you can
```

sudo dpkg --instdir=/path/to/new/root -i /var/cache/apt/archives/*.deb
sudo apt-get clean

```

---

### Post by monkeybrain2012 on 2013-02-14
R is very easy to compile. It is a lot easier to just compile it with the proper Prefix than to try to trick apt-get to do various weird things. 

Aside: I either compile R or use a ppa ([https://launchpad.net/~marutter/+archive/rrutter](https://launchpad.net/~marutter/+archive/rrutter)) Repo version is antique, don't even bother.

---

### Post by megamonk on 2013-02-14
> **schragge said:**
> Try this
```

sudo apt-get clean
sudo apt-get -d --reinstall install r-base `apt-cache --recurse -i depends r-base|awk '/Depends: /{gsub(/^<|>$/,"",$2);print$2}'|sort -u`

```The first command essentially *rm /var/cache/apt/archives/**. The second one recursively downloads *r-base* and all its dependencies into */var/cache/apt/archives/*, but stops short of (re)installing them.

After that you can
```

sudo dpkg --instdir=/path/to/new/root -i /var/cache/apt/archives/*.deb
sudo apt-get clean

```

tried

```

sudo apt-get clean
sudo apt-get -d --reinstall install r-base `apt-cache --recurse -i  depends r-base|awk '/Depends: /{gsub(/^<|>$/,"",$2);print$2}'|sort  -u`

```got:

```

ryanwork@ubuntu:~$ sudo apt-get -d --reinstall install r-base `apt-cache --recurse -i depends r-base|awk '/Depends: /{gsub(/^<|>$/,"",$2);print$2}'|sort -u`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'adduser' instead of 'adduser:i386'
Note, selecting 'debconf' instead of 'debconf:i386'
Note, selecting 'fontconfig-config' instead of 'fontconfig-config:i386'
Note, selecting 'initramfs-tools' instead of 'initramfs-tools:i386'
Note, selecting 'lsb-base' instead of 'lsb-base:i386'
Note, selecting 'makedev' instead of 'makedev:i386'
Note, selecting 'sensible-utils' instead of 'sensible-utils:i386'
Note, selecting 'sysv-rc' instead of 'sysv-rc:i386'
Note, selecting 'tzdata' instead of 'tzdata:i386'
Note, selecting 'upstart' instead of 'upstart-job'
Note, selecting 'upstart:i386' instead of 'upstart-job:i386'
Note, selecting 'x11-common' instead of 'x11-common:i386'
Note, selecting 'xfonts-encodings' instead of 'xfonts-encodings:i386'
Package debconf-2.0 is a virtual package provided by:
  debconf 1.5.46ubuntu1
  cdebconf 0.172ubuntu1
You should explicitly select one to install.

Package debconf-2.0:i386 is a virtual package provided by:
  cdebconf:i386 0.172ubuntu1
  debconf 1.5.46ubuntu1
You should explicitly select one to install.

Package file-rc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  sysv-rc

Package libblas.so.3 is a virtual package provided by:
  libopenblas-base 0.1.1-6
  libatlas3-base 3.8.4-8ubuntu1
  libblas3 1.2.20110419-5
You should explicitly select one to install.

Package libblas.so.3gf is a virtual package provided by:
  libatlas3-base 3.8.4-8ubuntu1
  libblas3 1.2.20110419-5
You should explicitly select one to install.

Package liblapack.so.3gf is a virtual package provided by:
  libatlas3-base 3.8.4-8ubuntu1
  liblapack3 3.4.1-6
You should explicitly select one to install.

Package liblapack.so.3 is a virtual package provided by:
  libatlas3-base 3.8.4-8ubuntu1
  liblapack3 3.4.1-6
You should explicitly select one to install.

Package file-rc:i386 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  sysv-rc

Package ucf:i386 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'debconf-2.0' has no installation candidate
E: Package 'debconf-2.0:i386' has no installation candidate
E: Package 'file-rc' has no installation candidate
E: Package 'file-rc:i386' has no installation candidate
E: Package 'libblas.so.3' has no installation candidate
E: Package 'libblas.so.3gf' has no installation candidate
E: Package 'liblapack.so.3' has no installation candidate
E: Package 'liblapack.so.3gf' has no installation candidate
E: Package 'ucf:i386' has no installation candidate

```I checked the folder /var/cache/apt/archives and its empty... :(

---

### Post by schragge on 2013-02-14
Well, try this instead
```

sudo apt-get clean
sudo apt-get -d --reinstall install r-base `apt-cache --recurse -i depends r-base [color=red]liblapack3[/color]|awk '$2!~/^(<|ucf|file-rc)/{print$2}'|sort -u`

```

But be aware that it downloads **all** dependencies, even the most basic ones. I'm getting 113 debs on Debian wheezy.

[color=blue]**Update**[/color].
Added liblapack3

---

