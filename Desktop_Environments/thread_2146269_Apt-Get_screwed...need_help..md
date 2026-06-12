---
title: "Apt-Get screwed...need help."
date: 2013-05-17
forum: Desktop Environments
---

### Post by pepsifx357 on 2013-05-17
I've got a laptop that can't update, install, or uninstall anything.  I have no idea what happened.

```
josh@Laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 initramfs-tools : Depends: initramfs-tools-bin (< 0.99ubuntu13.1~) but 0.99ubuntu13.1 is installed
E: Unmet dependencies. Try using -f.
```

```
josh@Laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  initramfs-tools
The following packages will be upgraded:
  initramfs-tools
1 upgraded, 0 newly installed, 0 to remove and 494 not upgraded.
10 not fully installed or removed.
Need to get 0 B/49.0 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of initramfs-tools:
 initramfs-tools depends on initramfs-tools-bin (<< 0.99ubuntu13.1~); however:
  Version of initramfs-tools-bin on system is 0.99ubuntu13.1.
dpkg: error processing initramfs-tools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of udev:
 udev depends on initramfs-tools (>= 0.92bubuntu63); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing udev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of plymouth:
 plymouth depends on udev (>= 166-0ubuntu4); however:
  Package udev is not configured yet.
 plymouth depends on initramfs-tools; however:
  Package initramfs-tools is not configured yet.
dpkg: error processing plymouth (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                               No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of mountall:
 mountall depends on udev; however:
  Package udev is not configured yet.
 mountall depends on plymouth; however:
  Package plymouth is not configured yet.
dpkg: error processing mountall (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of initscripts:
 initscripts depends on mountall (>= 2.28); however:
  Package mountall is not configured yet.
dpkg: error processing initscripts (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of upstart:
 upstart depends on initscripts; however:
  Package initscripts is not configured yet.
 upstart depends on mountall; however:
  Package mountall is not configured yet.
dpkg: error processing upstart (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of passwd:
 passwd depends on upstart-job; however:
  Package upstart-job isNo apport report written because MaxReports is reached already
                                                                                      No apport report written because MaxReports is reached already
                                                       No apport report written because MaxReports is reached already
                        No apport report written because MaxReports is reached already
                                                                                      No apport report written because MaxReports is reached already
                                                       No apport report written because MaxReports is reached already
                         not installed.
  Package upstart which provides upstart-job is not configured yet.
dpkg: error processing passwd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dmsetup:
 dmsetup depends on initramfs-tools; however:
  Package initramfs-tools is not configured yet.
 dmsetup depends on udev (>> 141-2); however:
  Package udev is not configured yet.
dpkg: error processing dmsetup (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of plymouth-label:
 plymouth-label depends on plymouth (= 0.8.2-2ubuntu31); however:
  Package plymouth is not configured yet.
dpkg: error processing plymouth-label (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libdevmapper1.02.1:
 libdevmapper1.02.1 depends on dmsetup (>= 2:1.02.48-4ubuntu7.3); however:
  Package dmsetup is not configured yet.
dpkg: error processing libdevmapper1.02.1 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 initramfs-tools
 udev
 plymouth
 mountall
 initscripts
 upstart
 passwd
 dmsetup
 plymouth-label
 libdevmapper1.02.1
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Can anyone tell me how to fix this?

Thanks

---

### Post by cprofitt on 2013-05-18
Here are some steps to try:

The first step I would suggest is:
[PHP]
sudo dpkg --configure --pending[/PHP]

Next I would try:
[PHP]sudo dpkg --configure -a[/PHP]

after that try the same command original recommended:

[PHP]sudo apt-get -f install[/PHP]

If that doesn't work you want to edit the following files:

> sudo gedit /var/lib/dpkg/status  

Remove all the lines pertaining to the problem package.

I hope those steps help... they did for me with a computer that my youngest shutdown while it was in the middle of an upgrade.

---

