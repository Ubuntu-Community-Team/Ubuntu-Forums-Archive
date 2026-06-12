---
title: "Help Prob wit AWN"
date: 2008-02-24
forum: Desktop Environments
---

### Post by balaji.c.86 on 2008-02-24
Tried to uninstall and make a clean install of AWN.

used the following command for the uninstallation process
"sudo apt-get remove avant-window-navigator avant-window-navigator-bzr awn-core-applets-bzr"

Ended up with an error MSG

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package avant-window-navigator-bzr is not installed, so not removed
Package awn-core-applets-bzr is not installed, so not removed
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  awn-manager: Depends: avant-window-navigator (>= 0.2)
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


When i Tried the "apt-get -f install" i end up with 


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package avant-window-navigator-bzr is not installed, so not removed
Package awn-core-applets-bzr is not installed, so not removed
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  awn-manager: Depends: avant-window-navigator (>= 0.2)
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
balaji@balaji-desktop:/$ apt-get -f instal
E: Invalid operation instal
balaji@balaji-desktop:/$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  python-libawn-bzr libawn-bzr
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libawn0
The following NEW packages will be installed:
  libawn0
0 upgraded, 1 newly installed, 0 to remove and 23 not upgraded.
2 not fully installed or removed.
Need to get 0B/67.2kB of archives.
After unpacking 197kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 114364 files and directories currently installed.)
Unpacking libawn0 (from .../libawn0_0.2.1-0ubuntu1~gutsy1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libawn0_0.2.1-0ubuntu1~gutsy1_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/libawn.so.0.0.1', which is also in package libawn-bzr
Errors were encountered while processing:
 /var/cache/apt/archives/libawn0_0.2.1-0ubuntu1~gutsy1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Help would be appreciated..
Regards 
Balaji C

---

### Post by Jussi Kukkonen on 2008-02-24
```
sudo apt-get install libawn0+ libawn-bzr-
sudo apt-get -f install
```

You'll still probably have some awn packages installed, but that should bring apt to a clean state.

EDIT: missed one package

---

### Post by balaji.c.86 on 2008-02-25
Thanks for the help...

Executed the above mentioned..
And removed the AWN ..

balaji@balaji-desktop:~$ dpkg --search avant-window-navigator
dpkg: *avant-window-navigator* not found.
balaji@balaji-desktop:~$ 


It would be of great help if i could get help on making a clean installation of AWN and some sources of additional applets that works fine... I work on a Core2duo. intel d945 board

Regards
Balaji C

---

