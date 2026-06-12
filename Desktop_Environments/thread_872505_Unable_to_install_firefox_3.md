---
title: "Unable to install firefox 3"
date: 2008-07-28
forum: Desktop Environments
---

### Post by arunprakasha on 2008-07-28
When i try to install firefox 3, it fails with the following error message. Looks like there is a broken package or am i missing something


-----------
$ sudo apt-get install firefox
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
  firefox: Depends: firefox-3.0 but it is not going to be installed
E: Broken packages

-----------
$ sudo apt-get install firefox-3.0
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
  firefox-3.0: Depends: libpango1.0-0 (>= 1.20.5) but 1.20.1-1 is to be installed
               Depends: xulrunner-1.9 (>= 1.9.0.1) but 1.9~rc1+nobinonly-0ubuntu1~8.04.2 is to be installed
E: Broken packages

-----------

--Arun

---

### Post by brujoand on 2008-07-28
Firefox 3.0 is now standard on Ubuntu 8.04, did you uninstall it?

---

### Post by arunprakasha on 2008-07-28
It happened that I have turned off the 'recommended update' in the updates tab of repository menu, hence the synaptic was not able to upgrade the libpango and other packages. Once I turned it ON, it upgraded the dependent package and installed the firefox package. 

Thanks to people who have responded to my query.

--Arun

---

