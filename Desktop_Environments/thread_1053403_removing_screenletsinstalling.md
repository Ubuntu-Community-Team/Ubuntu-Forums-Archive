---
title: "removing screenlets/installing"
date: 2009-01-28
forum: Desktop Environments
---

### Post by adonis9 on 2009-01-28
hey guys. i am trying to install screen-lets from update manager but this error is keep poping up again and again

(unable to iinstall new version of `./usr/share/dbus-1/services/org.screenlets.ScreenletsDaemon.service')

i try to remove the previous installation from synaptic package manager but there was another error msg it says..
(E: screen-lets: Package is in a very bad inconsistent state - you should)

please help
thanks in advance

---

### Post by XanTrax on 2009-01-28
> **adonis9 said:**
> hey guys. i am trying to install screen-lets from update manager but this error is keep poping up again and again

(unable to iinstall new version of `./usr/share/dbus-1/services/org.screenlets.ScreenletsDaemon.service')

i try to remove the previous installation from synaptic package manager but there was another error msg it says..
(E: screen-lets: Package is in a very bad inconsistent state - you should)

please help
thanks in advance

Please post the output of

```
sudo apt-get install --reinstall screenlets
```

---

### Post by adonis9 on 2009-01-29
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  python-dcop
The following packages will be upgraded:
  screenlets
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/2599kB of archives.
After this operation, 9089kB of additional disk space will be used.
Selecting previously deselected package screenlets.
(Reading database ... 
dpkg: serious warning: files list file for package `screenlets' missing, assuming package has no files currently installed.
139745 files and directories currently installed.)
Preparing to replace screenlets 0.1.2-3ubuntu1 (using .../screenlets_0.1.2-3ubuntu1_all.deb) ...
Unpacking replacement screenlets ...
dpkg: error processing /var/cache/apt/archives/screenlets_0.1.2-3ubuntu1_all.deb (--unpack):
 unable to install new version of `./usr/share/dbus-1/services/org.screenlets.ScreenletsDaemon.service': Is a directory
dpkg: error while cleaning up:
 unable to remove newly-installed version of `/usr/share/dbus-1/services/org.screenlets.ScreenletsDaemon.service' to allow reinstallation of backup copy: Directory not empty
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/screenlets_0.1.2-3ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by XanTrax on 2009-01-29
Please try these commands:

```
sudo rm -rfv /usr/share/dbus-1/services/org.screenlets.ScreenletsDaemon.service
sudo apt-get install --reinstall screenlets
sudo apt-get remove screenlets

```

and post the output please.

---

### Post by adonis9 on 2009-01-29
aijaz@ubuntu:~$ sudo rm -rfv /usr/share/dbus-1/services/org.screenlets.ScreenletsDaemon.service
aijaz@ubuntu:~$ sudo apt-get install --reinstall screenlets
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  python-dcop
The following packages will be upgraded:
  screenlets
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/2599kB of archives.
After this operation, 9089kB of additional disk space will be used.
(Reading database ... 
dpkg: serious warning: files list file for package `screenlets' missing, assuming package has no files currently installed.
140121 files and directories currently installed.)
Preparing to replace screenlets 0.1.2-3ubuntu1 (using .../screenlets_0.1.2-3ubuntu1_all.deb) ...
Unpacking replacement screenlets ...
Processing triggers for man-db ...
Setting up screenlets (0.1.2-3ubuntu1) ...

aijaz@ubuntu:~$ sudo apt-get remove screenlets
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  screenlets
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 9089kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 140996 files and directories currently installed.)
Removing screenlets ...
Processing triggers for man-db ...

---

### Post by XanTrax on 2009-01-29
> **adonis9 said:**
> aijaz@ubuntu:~$ sudo rm -rfv /usr/share/dbus-1/services/org.screenlets.ScreenletsDaemon.service
aijaz@ubuntu:~$ sudo apt-get install --reinstall screenlets
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  python-dcop
The following packages will be upgraded:
  screenlets
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/2599kB of archives.
After this operation, 9089kB of additional disk space will be used.
(Reading database ... 
dpkg: serious warning: files list file for package `screenlets' missing, assuming package has no files currently installed.
140121 files and directories currently installed.)
Preparing to replace screenlets 0.1.2-3ubuntu1 (using .../screenlets_0.1.2-3ubuntu1_all.deb) ...
Unpacking replacement screenlets ...
Processing triggers for man-db ...
Setting up screenlets (0.1.2-3ubuntu1) ...

aijaz@ubuntu:~$ sudo apt-get remove screenlets
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  screenlets
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 9089kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 140996 files and directories currently installed.)
Removing screenlets ...
Processing triggers for man-db ...

As I can see from here, deleting that file/folder, reinstalling, and then uninstalling seems to have accomplished what you wanted?  So, is this resolved?

---

### Post by adonis9 on 2009-01-29
thanks a lot problem is solved..........

---

### Post by XanTrax on 2009-01-29
> **adonis9 said:**
> thanks a lot problem is solved..........

Read your first post again, forgot you wanted to install it in the first place.

---

