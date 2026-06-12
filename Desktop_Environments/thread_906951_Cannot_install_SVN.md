---
title: "Cannot install SVN"
date: 2008-09-01
forum: Desktop Environments
---

### Post by watupgroupie on 2008-09-01
I need to install svn(subversion) to install a toolchain I want to use (which is beside the point) and when I try to install svn i get this error: ```
kent@DOWN:~$ sudo apt-get install subversion
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
The following information may help resolve the situation:

The following packages have unmet dependencies:
  subversion: Depends: libsvn1 (= 1.4.6dfsg1-2ubuntu1) but it is not going to be installed
E: Broken packages

```Can anyone please help me here?:)

---

### Post by mellowd on 2008-09-01
what happens if you try and install libsvn1 first?

---

### Post by watupgroupie on 2008-09-01
It fails, and tells you it needs a dependency as well, which ultimatly fails as well. Here's what it does:
```
kent@DOWN:~/Desktop/pspsdk$ sudo apt-get install libsvn1
[sudo] password for kent: 
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
The following information may help resolve the situation:

The following packages have unmet dependencies:
  libsvn1: Depends: libaprutil1 but it is not going to be installed
E: Broken packages
kent@DOWN:~/Desktop/pspsdk$ sudo apt-get install libaprutil1
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
The following information may help resolve the situation:

The following packages have unmet dependencies:
  libaprutil1: Depends: libpq5 (>= 8.3~beta1) but it is not going to be installed
E: Broken packages
```

---

### Post by watupgroupie on 2008-09-01
Sorry for double post, but I figured it out. I went and found the .deb files for these dependencies myself through google and installed them. Works fine now.

---

