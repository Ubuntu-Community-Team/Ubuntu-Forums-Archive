---
title: "package manager broken after kde install"
date: 2012-02-01
forum: Desktop Environments
---

### Post by scampbell70 on 2012-02-01
I am running Ubuntu 11.10 and I tried to install KDE using the following commands

[COLOR=Black][COLOR=#008080][I]sudo add-apt-repository ppa:kubuntu-ppa/backports
[/I][/COLOR][COLOR=#008080][I]sudo apt-get update
[/I][/COLOR][COLOR=#008080][I]
install kubuntu-desktop[/I][/COLOR] through software center[/COLOR]

It gets to the end of the install and errors out. Then it reports package manager is broken and to run sudo apt-get -f install I do and get this error

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libkactivities-bin
The following NEW packages will be installed:
  libkactivities-bin
0 upgraded, 1 newly installed, 0 to remove and 13 not upgraded.
11 not fully installed or removed.
Need to get 0 B/80.4 kB of archives.
After this operation, 401 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 271184 files and directories currently installed.)
Unpacking libkactivities-bin (from .../libkactivities-bin_4%3a4.8.0-0ubuntu1~oneiric1~ppa1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libkactivities-bin_4%3a4.8.0-0ubuntu1~oneiric1~ppa1_i386.deb (--unpack):
 trying to overwrite '/usr/share/kde4/services/kactivitymanagerd.desktop', which is also in package kde-runtime-data 4:4.7.4-0ubuntu0.1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libkactivities-bin_4%3a4.8.0-0ubuntu1~oneiric1~ppa1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


I also tried to install libkactivities-bin manually but it will not let me. 

Then I ran sudo apt-get autoremove kubuntu-desktop and got

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libkactivities6 : Depends: libkactivities-bin (= 4:4.8.0-0ubuntu1~oneiric1~ppa1) but it is not going to be installed
 plasma-desktop : Depends: libkactivities-bin but it is not going to be installed
 plasma-netbook : Depends: libkactivities-bin but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).



The full error is 

The package system is broken
Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f

The following packages have unmet dependencies:

libkactivities6: Depends: libkactivities-bin (= 4:4.8.0-0ubuntu1~oneiric1~ppa1) but it is not installed
plasma-desktop: Depends: libkephal4abi1 (= 4:4.8.0b-0ubuntu1~oneiric1~ppa1) but 4:4.8.0b-0ubuntu1~oneiric1~ppa1 is installed
                Depends: libkworkspace4abi1 (= 4:4.8.0b-0ubuntu1~oneiric1~ppa1) but 4:4.8.0b-0ubuntu1~oneiric1~ppa1 is installed
                Depends: libplasmagenericshell4 (= 4:4.8.0b-0ubuntu1~oneiric1~ppa1) but 4:4.8.0b-0ubuntu1~oneiric1~ppa1 is installed
                Depends: libtaskmanager4abi3 (= 4:4.8.0b-0ubuntu1~oneiric1~ppa1) but 4:4.8.0b-0ubuntu1~oneiric1~ppa1 is installed
                Depends: plasma-widgets-workspace (= 4:4.8.0b-0ubuntu1~oneiric1~ppa1) but 4:4.8.0b-0ubuntu1~oneiric1~ppa1 is installed
                Depends: libkactivities-bin but it is not installed
plasma-netbook: Depends: libkephal4abi1 (= 4:4.8.0b-0ubuntu1~oneiric1~ppa1) but 4:4.8.0b-0ubuntu1~oneiric1~ppa1 is installed
                Depends: libplasmagenericshell4 (= 4:4.8.0b-0ubuntu1~oneiric1~ppa1) but 4:4.8.0b-0ubuntu1~oneiric1~ppa1 is installed
                Depends: plasma-widgets-workspace (= 4:4.8.0b-0ubuntu1~oneiric1~ppa1) but 4:4.8.0b-0ubuntu1~oneiric1~ppa1 is installed
                Depends: libkactivities-bin but it is not installed


can anyone please help me fix this??

---

### Post by jerrrys on 2012-02-03
Check if you are using third party repositories. If so disable them, since they are a common source of problems.

Did you do that?  Also should try:  sudo apt-get clean

---

### Post by drmrgd on 2012-02-03
Also, what happens when you follow the instructions from the error message and run:

```
sudo apt-get -f install
```

---

### Post by scampbell70 on 2012-02-05
I was not online for a few days and just got back on and there were some updating wanting to be installed and I clicked install. I expected them to fail as it has been but it went through and there does not appear to be any errors at this time. The only thing I did was turn off the computer after I couldnt fix it issue. Is it possible that rebooting it fixed it somehow?

---

