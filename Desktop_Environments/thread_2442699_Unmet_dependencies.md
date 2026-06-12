---
title: "Unmet dependencies"
date: 2020-05-06
forum: Desktop Environments
---

### Post by geomcd1949 on 2020-05-06
```
"Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f
Transaction failed: The package system is broken
 The following packages have unmet dependencies:

mysql-server-8.0: Depends: mysql-client-8.0 (>= 8.0.19-0ubuntu5) but 8.0.20-0ubuntu0.20.04.1 is installed
                  Depends: mysql-server-core-8.0 (= 8.0.19-0ubuntu5) but 8.0.20-0ubuntu0.20.04.1 is installed
                  Depends: perl:any (>= 5.6) but it is a virtual package"
```
-------
[B]Third-party repositories are disabled.

Sudo apt-get install -f gives:[/B]

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  mysql-server-8.0
Suggested packages:
  tinyca
The following packages will be upgraded:
  mysql-server-8.0
1 upgraded, 0 newly installed, 0 to remove and 35 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1,228 kB of archives.
After this operation, 14.3 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Preconfiguring packages ...
(Reading database ... 257689 files and directories currently installed.)
Preparing to unpack .../mysql-server-8.0_8.0.20-0ubuntu0.20.04.1_amd64.deb ...
Failed to stop mysql.service: Unit mysql.service not loaded.
invoke-rc.d: initscript mysql, action "stop" failed.
dpkg: warning: old mysql-server-8.0 package pre-removal script subprocess returned error exit status 1
dpkg: trying script from the new package instead ...
Failed to stop mysql.service: Unit mysql.service not loaded.
invoke-rc.d: initscript mysql, action "stop" failed.
dpkg: error processing archive /var/cache/apt/archives/mysql-server-8.0_8.0.20-0ubuntu0.20.04.1_amd64.deb (--unpack):
 new mysql-server-8.0 package pre-removal script subprocess returned error exit status 1
Failed to stop mysql.service: Unit mysql.service not loaded.
invoke-rc.d: initscript mysql, action "stop" failed.
Failed to preset unit: File mysql.service: Link has been severed
/usr/bin/deb-systemd-helper: error: systemctl preset failed on mysql.service: No such file or directory
Failed to start mysql.service: Unit mysql.service not found.
invoke-rc.d: initscript mysql, action "start" failed.
Unit mysql.service could not be found.
dpkg: error while cleaning up:
 installed mysql-server-8.0 package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-8.0_8.0.20-0ubuntu0.20.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by geomcd1949 on 2020-05-06
This problem was fixed by [I think} a software update from Ubuntu 20.04.

---

