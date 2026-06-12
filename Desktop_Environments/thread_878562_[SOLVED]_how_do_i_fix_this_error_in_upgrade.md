---
title: "[SOLVED] how do i fix this error in upgrade"
date: 2008-08-03
forum: Desktop Environments
---

### Post by ramaswamyps on 2008-08-03
root@ubuntu:~# apt-get -f install --fix-broken                        
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  kde-window-manager
The following NEW packages will be installed:
  kde-window-manager
0 upgraded, 1 newly installed, 0 to remove and 88 not upgraded.
4 not fully installed or removed.
Need to get 0B/1394kB of archives.
After this operation, 4477kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  kde-window-manager
Install these packages without verification [y/N]? y
(Reading database ... 181309 files and directories currently installed.)
Unpacking kde-window-manager (from .../kde-window-manager_4%3a4.1.0-0ubuntu1~hardy1~ppa2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/kde-window-manager_4%3a4.1.0-0ubuntu1~hardy1~ppa2_i386.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/share/doc/kde4/HTML/en/kcontrol/kwindecoration/index.docbook', which is also in package kdebase-runtime-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kde-window-manager_4%3a4.1.0-0ubuntu1~hardy1~ppa2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:~#
--------------------------------------------------------

the above is error report 
synaptic also gives error 1 output.
i installed kde-4.1 in ubuntu-studio-8.04
now it is getting stuck at this error.
kde-4.1 is working.
but apt-get upgrade gets stuck here.
help required

---

### Post by sayakb on 2008-08-03
Try:
```
sudo mv /usr/lib/kde4/share/doc/kde4/HTML/en/kcontrol/kwindecoration/index.docbook /usr/lib/kde4/share/doc/kde4/HTML/en/kcontrol/kwindecoration/index.docbook~

sudo apt-get install -f
```

Also, 
```
sudo apt-get install kde-window-manager
```

---

### Post by ramaswamyps on 2008-08-03
thanks for the advice.
i would like to know why moving the file became necessary?
the newer files are supposed to replace the old ones i thought.
in the meanwhile i updated with adept also.
currently there is no broken package and system uptodate.
thanks very much LinuxIsInnovation:):)

---

