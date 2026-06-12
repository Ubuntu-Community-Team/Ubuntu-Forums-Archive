---
title: "Dependency issue"
date: 2005-11-18
forum: Desktop Environments
---

### Post by MagicMirari on 2005-11-18
I'm having problems installing anything using apt-get install:

```
The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.3.5-1ubuntu12) but 2.3.2.ds1-20ubuntu13 is installed
             Depends: linux-kernel-headers (>= 2.6.11.2-0) but 2.5.999-test7-bk-17 is installed

```

This is for everything I've tried to install, besides what I couldn't find a package for.

Anyone have any idea?
I tried downloading a new disk, maybe the install went bad, but it would only burn 1/2   the disk, and claim it was finished.  (The original disk used is far far away)

Any help, thanks in advance.

---

### Post by Original Brownster on 2005-11-18
Hi,
Could you provide a little more information please? 
It looks like you have ubuntu installed already and are trying to bring the system upto date, or maybe your just trying to install a / some new packages? If so what's the current version installed.

Things you can try:

ensure your /etc/apt/sources.list  contains a list of the repositorys for the edition you have. ie like this for Breezy:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
 
make sure the repository is upto date:

$ sudo apt-get update

if you still have a problem, try:

$ sudo apt-get install -f

(this will attempt to fix broken dependencies)

HTH

---

### Post by dcstar on 2005-11-19
[QUOTE=MagicMirari]I'm having problems installing anything using apt-get install:

```
The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.3.5-1ubuntu12) but 2.3.2.ds1-20ubuntu13 is installed
             Depends: linux-kernel-headers (>= 2.6.11.2-0) but 2.5.999-test7-bk-17 is installed

```

This is for everything I've tried to install, besides what I couldn't find a package for.

Anyone have any idea?
I tried downloading a new disk, maybe the install went bad, but it would only burn 1/2   the disk, and claim it was finished.  (The original disk used is far far away)

Any help, thanks in advance.[/QUOTE]
You need the latest libc6 package, and the latest linux-kernel-headers.

If you are not offered them by Synaptic, you may need to change your Repositories to look in the additional places where these may reside.

The FAQ of enabling additional repositories may be your first port of call.

---

