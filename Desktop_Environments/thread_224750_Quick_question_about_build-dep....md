---
title: "Quick question about build-dep..."
date: 2006-07-28
forum: Desktop Environments
---

### Post by roostishaw on 2006-07-28
Hello,
I'm currently trying to get Network Manager set up (again, it suddenly broke itself), with WPA & WPA2 support. I'm following the guide from the forums [here]("http://ubuntuforums.org/showthread.php?t=125150&highlight=wpa+atheros"). A few times during the guide, it tells me to run:
```
sudo apt-get build-dep [package name]
```
But after running the above, with the specified package of course, I get the following output:
```
[ ~ ] sudo apt-get build-dep [package name]
Reading package lists... Done
Building dependency tree... Done
E: Build-dependencies for [package name] could not be satisfied.
```
I run 'sudo apt-get update' every day, as part of an update script I run. Also, I've been told that it has to do with my sources file. Below is my sources.list:
```
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src http://archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse

# For Gaim Beta2
deb http://idefix.eup.uva.es/paquetes/gaim2.0/ ./
```

If you know anything about this problem, or need any more info, reply here with what's needed.
Thanks!

---

### Post by roostishaw on 2006-08-05
Anyone?
The only other option I have is to reinstall... :(

---

