---
title: "cpp fails sanity check ||| build-essential no installation candidate"
date: 2006-08-12
forum: Desktop Environments
---

### Post by _axiom_ on 2006-08-12
I changed all the http links to ftp links in my sources.list, and it works now.  Per this post.
[http://www.ubuntuforums.org/archive/index.php/t-9944.html](http://www.ubuntuforums.org/archive/index.php/t-9944.html)




Everywhere I read that I must install build-essential before I can complile anyting ( which I can't).

Why does build-essential not install?  Have they changed the name?

I see it here:
[http://packages.ubuntu.com/dapper/devel/build-essential](http://packages.ubuntu.com/dapper/devel/build-essential)

This is what happens to me:

```
$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package build-essential has no installation candidate

```


Just for kicks

```

$ cat /etc/apt/sources.list
deb http://kubuntu.org/packages/kde-354 dapper main

##deb http://kubuntu.org/packages/kde-353 dapper main


# Example sources.list for Ubuntu 5.10 "The Breezy Badger" release

## All officially supported packages, including security- and other updates
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted

## The source pacakges
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

## All community supported packages, including security- and other updates
deb http://archive.ubuntu.com/ubuntu dapper universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse

## The source pacakges
deb-src http://archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse

## hoary-extras - the most widely used source for packages not includded in Ubuntu
## no guarantees on working - not enabled by default
# deb http://public.planetmirror.com/pub/ubuntu-backports/ hoary-extras main universe multiverse restricted

# deb http://wine.sourceforge.net/apt/ binary/
# deb-src http://wine.sourceforge.net/apt/ source/


# deb http://kanotix.com/files/debian/ ./

# deb http://seveas.ubuntulinux.nl/ breezy-seveas all
# deb-src http://seveas.ubuntulinux.nl/ breezy-seveas all

# deb http://people.ubuntu.com/~jbailey/snapshot/bzr ./

# deb http://people.ubuntu.com/~doko/OOo2 ./

# deb http://kubuntu.org/packages/kde35 breezy main

# deb http://people.ubuntu.com/~doko/OOo2 ./

# deb http://kubuntu.org/packages/koffice-15 breezy main


# deb http://repo.nanofreesoft.org/ubuntu breezy main

```

---

### Post by davidsxls on 2006-08-12
try 
$ sudo apt-get update 

if it's completed successfully
$ sudo apt-get install build-essential

---

