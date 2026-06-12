---
title: "Installing postgresql-8.2 on Ubuntu 8.04 Hardy &quot;but it is not installable&quot; error"
date: 2008-12-13
forum: General Help
---

### Post by mnemonik on 2008-12-13
```
mnemonik@mnemonik-laptop:~$ sudo apt-get install postgresql-8.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  postgresql-8.2: Depends: postgresql-client-8.2 but it is not going to be installed
                  Depends: postgresql-common (>= 63) but it is not installable
E: Broken packages


```

This is the error I get when trying to install postgresql-8.2 through the terminal. When I try to install it through the synaptic package manager I get a similar error. I read through some google searches that had the same error but trying to install different things. They said to remove the files the error is referring to because they might just be a different version than the dependency requires but they aren't installed at all so that goes nowhere. I'm a bit of a ubuntu novice, so any help is greatly appreciated.

Thanks!

---

### Post by Bachstelze on 2008-12-13
What happens when you do this?

```
sudo apt-get install postgresql-client-8.2
```

---

### Post by mnemonik on 2008-12-13
> **HymnToLife said:**
> What happens when you do this?

```
sudo apt-get install postgresql-client-8.2
```

```
mnemonik@mnemonik-laptop:~$ sudo apt-get install postgresql-client-8.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  postgresql-client-8.2: Depends: postgresql-client-common but it is not installable
E: Broken packages

```

and when I try to run "sudo apt-get install postgresql-client-common" i get this:
```
mnemonik@mnemonik-laptop:~$ sudo apt-get install postgresql-client-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package postgresql-client-common is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package postgresql-client-common has no installation candidate

```

---

### Post by Bachstelze on 2008-12-13
Most likely you have a problem with your sources.list. Could you please paste it? (gedit /etc/apt/sources.list)

---

### Post by mnemonik on 2008-12-13
I just googled postgresql-client-common and came up with this:

[http://packages.debian.org/unstable/misc/postgresql-client-common](http://packages.debian.org/unstable/misc/postgresql-client-common)

So i guess it allows you to run two versions of postgresql but I don't want to do that, I just want to run 8.2! This got me thinking maybe some version of postgresql is already installed, so I ran "sudo apt-get remove postgresql" but got a standard "it isn't installed" message...

---

### Post by mnemonik on 2008-12-13
> **HymnToLife said:**
> Most likely you have a problem with your sources.list. Could you please paste it? (gedit /etc/apt/sources.list)

Here it is:

```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/ hardy main restricted
deb-src http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/ hardy-updates main restricted
deb-src http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/ hardy universe
deb-src http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/ hardy universe
deb http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/ hardy-updates universe
deb-src http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/ hardy multiverse
deb-src http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/ hardy multiverse
deb http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/ hardy-updates multiverse
deb-src http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/ hardy-security main restricted
deb-src http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/ hardy-security main restricted
deb http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/ hardy-security universe
deb-src http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/ hardy-security universe
deb http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/ hardy-security multiverse
deb-src http://ftp.caliu.info/pub/distribucions/ubuntu/ubuntu/ hardy-security multiverse
deb http://wine.budgetdedicated.com/apt hardy main #WineHQ
deb http://snapshot.debian.net/archive pool postgresql-8.2
deb-src http://snapshot.debian.net/archive pool postgresql-8.2
```

---

### Post by Bachstelze on 2008-12-13
Delete those two last lines. Why did you add them in the first place? They're for Debian, not Ubuntu.

---

### Post by mnemonik on 2008-12-13
> **HymnToLife said:**
> Delete those two last lines. Why did you add them in the first place? They're for Debian, not Ubuntu.

I guess I got confused somewhere along the lines of trying to get all the dependencies to get a reddit clone up and running. I'm pretty new to ubuntu and linux. I was using XP exclusively until just a few days ago when I finally got my wireless working in ubuntu. Ah well...

Let me try this out real quick...

---

### Post by mnemonik on 2008-12-13
Thanks a bunch, I got everything installed now!

---

