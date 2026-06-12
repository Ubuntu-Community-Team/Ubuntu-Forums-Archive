---
title: "A little help please :D"
date: 2007-08-22
forum: Dell  Ubuntu Support
---

### Post by Viruss on 2007-08-22
Errors were encountered while processing:
 clvm
 redhat-cluster-suite
 system-config-cluster
E: Sub-process /usr/bin/dpkg returned an error code (1)

I was attempting to install clamAV.

Fetched 177kB in 0s (199kB/s)        
debconf: unable to initialize frontend: Kde
debconf: (Unable to load Qt -- is libqt-perl installed?)
debconf: falling back to frontend: Dialog
Selecting previously deselected package clamav-daemon.
(Reading database ... 127315 files and directories currently installed.)
Unpacking clamav-daemon (from .../clamav-daemon_0.90.2-0ubuntu1.3_i386.deb) ...
Setting up clvm (2.02.06-2ubuntu9) ...
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error processing clvm (--configure):
 subprocess post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of redhat-cluster-suite:
 redhat-cluster-suite depends on clvm; however:
  Package clvm is not configured yet.
dpkg: error processing redhat-cluster-suite (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-cluster:
 system-config-cluster depends on redhat-cluster-suite; however:
  Package redhat-cluster-suite is not configured yet.
dpkg: error processing system-config-cluster (--configure):
 dependency problems - leaving unconfigured
Setting up clamav-daemon (0.90.2-0ubuntu1.3) ...
 * Starting ClamAV daemon clamd                                                 Running as user clamav (UID 113, GID 122)
                                                                         [ OK ]

Errors were encountered while processing:
 clvm
 redhat-cluster-suite
 system-config-cluster
E: Sub-process /usr/bin/dpkg returned an error code (1)

I am not sure what to do to remedy this issue. I have seen errors for dpkg all day :(

---

### Post by PaulFr on 2007-08-23
AFAICS, your problems do not seem to have anything to do with clamav, which was installed properly. They seem to be coming from your incomplete installation of **clvm, redhat-cluster-suite and system-config-cluster** as indicated in your installation. I would suggest you first remove those three packages using ```
sudo apt-get remove clvm redhat-cluster-suite system-config-cluster
```

---

