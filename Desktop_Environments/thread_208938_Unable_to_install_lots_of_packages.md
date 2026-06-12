---
title: "Unable to install lots of packages"
date: 2006-07-04
forum: Desktop Environments
---

### Post by NunoCorreia on 2006-07-04
I've been having lots of trouble with apt-get lately. I can't install many packages due to unmet packages and some of them are quite trivial (kubuntu-desktop being the most obvious example). There's [this](http://ubuntuforums.org/showthread.php?p=1212876#post1212876), too.

```
$ sudo apt-get -f install kubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  kubuntu-desktop: Depends: kdegraphics-kfile-plugins but it is not going to be installed
E: Broken packages

```

Here's my /etc/apt/sources.list

```

# Automatically generated sources.list
# http://www.ubuntulinux.nl/source-o-matic
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

deb http://pt.archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://pt.archive.ubuntu.com/ubuntu dapper main restricted

deb http://pt.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://pt.archive.ubuntu.com/ubuntu dapper-updates main restricted

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://pt.archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://pt.archive.ubuntu.com/ubuntu dapper universe multiverse

deb http://pt.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb-src http://pt.archive.ubuntu.com/ubuntu dapper-updates universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

```
I'd post this over at Repository Support, but this looks like it's my own problem since everyone else seems to be able to install at least kubuntu-desktop.

---

### Post by precinto on 2006-07-04
Have you tried repairing the brocken package?

Go to Synaptic: Edit/Repair broken packages.
Or you can select the Custom view and then the Broken filter...

---

### Post by NunoCorreia on 2006-07-04
That didn't work. No package showed up in the Synaptic listing when I selected the "broken" filter, although the status bar said success when I selected "Fix broken packages".

---

### Post by NunoCorreia on 2006-07-04
Turned out the problem was because I once had the beerorkid.net and xgl.compiz.info repositories enabled once for installing XGL and Compiz and removed them after. I think I might have fixed this by performing

```
$ sudo apt-get update && sudo apt-cache gencaches
```

Do you have anything else to add?

---

