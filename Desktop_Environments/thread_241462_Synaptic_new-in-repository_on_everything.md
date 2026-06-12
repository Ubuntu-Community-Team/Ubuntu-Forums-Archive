---
title: "Synaptic new-in-repository on everything"
date: 2006-08-22
forum: Desktop Environments
---

### Post by HAARP on 2006-08-22
Hi there,
I've changed the official repositories to some language specific server and that made almost every package to be marked as new-in-repository after I updated package information. I changed it back by now, but it's still like this, even after updating package information again. Is there any way to reset this?

sources.list:
```
# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu dapper universe multiverse
deb http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src http://archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Ubuntu commercial packages (packages)
deb http://archive.canonical.com/ubuntu dapper-commercial main

# Seveas' packages (packages, GPG key: 1135D466)
deb http://mirror3.ubuntulinux.nl dapper-seveas all
# Seveas' packages (sources, GPG key: 1135D466)
deb-src http://seveas.theplayboymansion.net/seveas dapper-seveas all

# Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
deb ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main
# Cipherfunk multimedia packages (sources, GPG key: 33BAC1B3)
deb-src ftp://cipherfunk.org/pub/packages/ubuntu dapper main

# Penguin Liberation Front (packages)
deb http://packages.freecontrib.org/plf dapper free non-free
# Penguin Liberation Front (sources)
deb-src http://packages.freecontrib.org/plf dapper free non-free

# Wine (packages)
deb http://wine.budgetdedicated.com/apt dapper main
# Bleeding edge Wine packages (sources)
deb-src http://wine.budgetdedicated.com/apt dapper main

# Opera (packages)
deb http://deb.opera.com/opera etch non-free

# Bazaar-NG development (packages, GPG key: 1F44842D)
deb http://people.ubuntu.com/~jbailey/snapshot/bzr ./
# Bazaar-NG development (sources, GPG key: 1F44842D)
deb-src http://people.ubuntu.com/~jbailey/snapshot/bzr ./

# Doomsday Engine (packages, GPG key: 4B6E7209)
deb http://eyagi.bpa.nu/~jamie/ubuntu dapper main restricted universe multiverse
# Doomsday Engine (sources, GPG key: 4B6E7209)
deb-src http://eyagi.bpa.nu/~jamie/ubuntu dapper main restricted universe multiverse

# Spring (packages)
deb ftp://ftp.gwdg.de/pub/linux/people/fbo/debspring/dapper/ /

# Skype (packages)
deb http://download.skype.com/linux/repos/debian/ stable non-free

#Asher256's packages (packages)
deb http://asher256-repository.tuxfamily.org dapper main dupdate french
deb http://asher256-repository.tuxfamily.org ubuntu main dupdate french

#Ubuntu Lite (packages)
deb http://blueeyedcreature.net/ubuntu ./
```

---

### Post by matthew on 2006-08-22
> **HAARP said:**
> Hi there,
I've changed the official repositories to some language specific server and that made almost every package to be marked as new-in-repository after I updated package information. I changed it back by now, but it's still like this. Is there any way to reset this?
If you hit "reload" it will download the lists of packages again, compare it to the list you have now, and unmark all the ones that exist currently...

---

### Post by HAARP on 2006-08-22
> **matthew said:**
> If you hit "reload" it will download the lists of packages again, compare it to the list you have now, and unmark all the ones that exist currently...

Well, actually it's not :/

---

### Post by HAARP on 2006-08-22
Solution:
Delete **/root/.synaptic/options**

---

### Post by warjowuch on 2006-10-29
Thanks, I just had the same weird problem. Is there a 'real' solution for this, I mean, what could cause this?

---

