---
title: "gnome problem, please help"
date: 2006-07-22
forum: Desktop Environments
---

### Post by FreDeas on 2006-07-22
HI. Yesterday I did some stupid things that include adding ubuntu LTS something in the update repository, installing some updates and programs and removing some stuff from my pc (including power management sth). The outcome is that in the boot screen at startup shows an extra option (kernel 2..... amd_64 server) (up to then I only had various amd_64 generiv kernels) when I choosed anything I was prompted for passwd and logged in an empty screen where nothing ever happened!
  I logged in using falisafe command prompt and sudo apt-get install gnome and then the promblem fixed, now I can logg in. Then I uninstall amd_64 server Kernel using the synaptic (which removed the new start up option) but ended up with an error sth about clvm. I also unmarked the repo I added in the updated (if I remember correctly).
  Anyway, now the update manager says "ERROR: BROKEN COUNT > 0" and prompts me to use either synaptic or sudo apt-get install -f. I did the last one and got this :

marinos@marinos-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies...Done
The following extra packages will be installed:
  linux-image-2.6.15-23-amd64-server
Recommended packages:
  lilo
The following packages will be REMOVED
  clvm
The following NEW packages will be installed
  linux-image-2.6.15-23-amd64-server
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 21.5MB of archives.
After unpacking 86.3MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.

also I tried to remove clvm and got this :

marinos@marinos-desktop:~$ sudo apt-get remove clvm
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED
  clvm
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 512kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 135565 files and directories currently installed.)
Removing clvm ...
Stopping Cluster LVM Daemon invoke-rc.d: initscript clvm, action "stop" failed.
dpkg: error processing clvm (--remove):
 subprocess pre-removal script returned error exit status 1
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 3
Errors were encountered while processing:
 clvm
E: Sub-process /usr/bin/dpkg returned an error code (1)

Synaptic also prompt to perform broken filter

  I don't want amd_64 server, what can I do to roll back ubuntu in its normal state??

PS, I also noticed that ubuntu-desktop is not installed I tried to install it but it post an error that can't remove clvm and the proccess is terminated..

---

### Post by FreDeas on 2006-07-22
I also noticed that I can't install anything, it tries to remove clvm, posts an error and then the proccess is terminated

---

