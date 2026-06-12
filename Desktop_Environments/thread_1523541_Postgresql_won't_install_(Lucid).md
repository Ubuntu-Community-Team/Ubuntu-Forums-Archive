---
title: "Postgresql won't install (Lucid)"
date: 2010-07-03
forum: Desktop Environments
---

### Post by awmian on 2010-07-03
Hi. I recently upgraded from Hardy LTS to Lucid LTS.  I am trying to install Postgresql but am unable to. The following error message comes up.
> asad@asad-laptop:~$ sudo apt-get install postgresql
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  postgresql: Depends: postgresql-8.4 but it is not going to be installed
E: Broken packages

Would appreciate if someone could help me with this.

---

### Post by awmian on 2010-07-03
I gave the following command and got this output:
> asad@asad-laptop:~$ sudo apt-get install postgresql-8.4
[sudo] password for asad: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  postgresql-8.4: Depends: libkrb53 (>= 1.6.dfsg.2) but it is not installable
                  Depends: libpq5 (>= 8.4~0cvs20090328) but it is not going to be installed
                  Depends: postgresql-client-8.4 but it is not going to be installed
E: Broken packages

It seems libkrb53 has been replaced with libkrb5-3 since Karmic, but the dependencies of root packages which depend upon this library aren't updated, so we have broken dependencies. 

Can anyone help me with a work around this problem?

---

### Post by awmian on 2010-07-04
Solved.  The work around is to install the deb package for libkrb53.  This can be obtained from:
[http://http://packages.debian.org/en/lenny/i386/libkrb53/download]("http://http://packages.debian.org/en/lenny/i386/libkrb53/download")

---

