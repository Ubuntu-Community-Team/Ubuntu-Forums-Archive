---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2014-09-14
forum: Desktop Environments
---

### Post by Muhammad_Ahmad_Mujtaba on 2014-09-14
> sudo apt-get -f install
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  shotwell
The following NEW packages will be installed
  shotwell
0 to upgrade, 1 to newly install, 0 to remove and 0 not to upgrade.
120 not fully installed or removed.
Need to get 8,196 kB of archives.
After this operation, 40.9 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://ppa.launchpad.net/yorba/daily-builds/ubuntu/](http://ppa.launchpad.net/yorba/daily-builds/ubuntu/) trusty/main shotwell amd64 0.19.0+2608~ubuntu14.04.1 [8,196 kB]
Fetched 8,196 kB in 2min 1s (67.7 kB/s)                                        
(Reading database ... 249086 files and directories currently installed.)
Preparing to unpack .../shotwell_0.19.0+2608~ubuntu14.04.1_amd64.deb ...
Unpacking shotwell (0.19.0+2608~ubuntu14.04.1) ...
dpkg: error processing archive /var/cache/apt/archives/shotwell_0.19.0+2608~ubuntu14.04.1_amd64.deb (--unpack):
 trying to overwrite '/usr/share/appdata/shotwell.appdata.xml', which is also in package shotwell-common 0.18.0-0ubuntu4.2
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for software-center (13.10-0ubuntu4.1) ...
INFO:softwarecenter.db.update:translation information in database is up-to-date
Processing triggers for menu (2.1.46ubuntu1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/shotwell_0.19.0+2608~ubuntu14.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



How do solve these errors? I know shotwell_0.19.0+2608~ubuntu14.04.1_amd64.deb is troubling here but how can i resolve it?

---

### Post by Muhammad_Ahmad_Mujtaba on 2014-09-14
[http://askubuntu.com/questions/504687/problem-while-updating-shotwell](http://askubuntu.com/questions/504687/problem-while-updating-shotwell)

from this link I was able to resolve this problem! I just used my version of shotwell than given on the link and hurray!

---

