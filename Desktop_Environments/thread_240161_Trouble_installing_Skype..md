---
title: "Trouble installing Skype."
date: 2006-08-20
forum: Desktop Environments
---

### Post by Sunnz on 2006-08-20
I have read the Ubuntu Skype and added Skype to the apt repo... but as I try to install Skype, it gave the following error::```
$ sudo apt-get install skype
Password:
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
  skype: Depends: libstdc++5 (>= 1:3.3.4-1) but it is not installable
  E: Broken packages
```How do I go solve this?

I am actually helping my friend to install it, and I only get to see him once a week... so I won't be able to try anything untill next Sunday.

---

### Post by linuxnewbie946 on 2006-08-20
> **Sunnz said:**
> I have read the Ubuntu Skype and added Skype to the apt repo... but as I try to install Skype, it gave the following error::```
$ sudo apt-get install skype
Password:
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
  skype: Depends: libstdc++5 (>= 1:3.3.4-1) but it is not installable
  E: Broken packages
```How do I go solve this?

I am actually helping my friend to install it, and I only get to see him once a week... so I won't be able to try anything untill next Sunday.


Try this:
```
sudo apt-get build-dep skype -y && sudo apt-get install skype -y
```

If it doesn't work try installing skype through automatix(program).

---

