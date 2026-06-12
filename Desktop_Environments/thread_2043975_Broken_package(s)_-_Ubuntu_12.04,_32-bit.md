---
title: "Broken package(s) - Ubuntu 12.04, 32-bit"
date: 2012-08-17
forum: Desktop Environments
---

### Post by steffanllyn on 2012-08-17
I'm trying to run software updater but get a message saying "The package system is broken

It goes on to elaborate...

"If you are using third party repositories then disable them, since they are a common source of problems.
Now run the following command in a terminal: apt-get install -f

The following packages have unmet dependencies:

libnux-2.0-0: Depends: libnux-2.0-common (= 2.12.0-0ubuntu1) but 2.14.0-0ubuntu1 is installed
              Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is installed
              Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but 2.26.1-1 is installed
              Depends: libglib2.0-0 (>= 2.31.8) but 2.32.3-0ubuntu1 is installed
              Depends: libpcre3 (>= 8.10) but 8.12-4 is installed
              Depends: libstdc++6 (>= 4.6) but 4.6.3-1ubuntu5 is installed"


However, when I run 'sudo apt-get install -f' I get...

The following extra packages will be installed:
  libnux-2.0-0
The following packages will be upgraded:
  libnux-2.0-0
1 upgraded, 0 newly installed, 0 to remove and 15 not upgraded.
Need to get 0 B/908 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 323998 files and directories currently installed.)
Preparing to replace libnux-2.0-0 2.12.0-0ubuntu1 (using .../libnux-2.0-0_2.14.0-0ubuntu1_i386.deb) ...
Unpacking replacement libnux-2.0-0 ...
dpkg: error processing /var/cache/apt/archives/libnux-2.0-0_2.14.0-0ubuntu1_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
No apport report written because MaxReports has already been reached
                                                                    dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libnux-2.0-0_2.14.0-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
 
Could anyone suggest how I can fix this?

---

### Post by TDalton on 2012-08-17
I've got similar problems. Any insight would be appreciated

---

### Post by steffanllyn on 2012-08-28
> **TDalton said:**
> I've got similar problems. Any insight would be appreciated

Running 'sudo apt-get clean' followed by 'sudo apt-get install -f' seemed to resolve the problem

---

