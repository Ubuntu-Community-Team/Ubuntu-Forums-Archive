---
title: "Errors while apt-get install banshee and muine."
date: 2006-06-18
forum: Desktop Environments
---

### Post by Tobbz on 2006-06-18
Hi all.

I can't figure out why i am getting the following errors, when trying to apt-get install banshee or muine.

```

~$ sudo apt-get install muine
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

The following packages have unmet dependencies:
  muine: Depends: libid3tag0 (>= 0.15.1b) but it is not installable
         Depends: mono-jit (>= 1.0) but it is not installable
         Depends: libdbus-1-cil (>= 0.60) but it is not installable
         Depends: libgconf2.0-cil (>= 2.7.90) but it is not installable
         Depends: libglade2.0-cil (>= 2.7.90) but it is not installable
         Depends: libglib2.0-cil (>= 2.7.90) but it is not installable
         Depends: libgnome2.0-cil (>= 2.7.90) but it is not installable
         Depends: libgtk2.0-cil (>= 2.7.90) but it is not installable
         Depends: mono-classlib-1.0 (>= 1.0) but it is not installable
E: Broken packages

```

or banshee:
```

$ sudo apt-get install banshee
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

The following packages have unmet dependencies:
  banshee: Depends: mono-jit (>= 1.0) but it is not installable
           Depends: libdbus-1-cil (>= 0.60) but it is not installable
           Depends: libgconf2.0-cil (>= 2.7.90) but it is not installable
           Depends: libglade2.0-cil (>= 2.7.90) but it is not installable
           Depends: libglib2.0-cil (>= 2.7.90) but it is not installable
           Depends: libgnome2.0-cil (>= 2.7.90) but it is not installable
           Depends: libgtk2.0-cil (>= 2.7.90) but it is not installable
           Depends: mono-classlib-1.0 (>= 1.0) but it is not installable
           Depends: gstreamer0.10-plugins-ugly but it is not going to be instal led
E: Broken packages

```

TIA

---

### Post by Ramses de Norre on 2006-06-18
What are your sources? I checked one of them and the right version was in a main repo..

---

### Post by Tobbz on 2006-06-18
Thanks for your reply.

I'm using:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse

---

### Post by Ramses de Norre on 2006-06-18
You'll want to add "main" and "restricted" too =)

---

### Post by Tobbz on 2006-06-18
Sorry.. I didn't show them all.

```

deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://au.archive.ubuntu.com/ubuntu/ dapper universe
# deb-src http://au.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://au.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```

---

### Post by Ramses de Norre on 2006-06-18
```
deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper universe multiverse
```

Add main and restricted to these two lines.

---

