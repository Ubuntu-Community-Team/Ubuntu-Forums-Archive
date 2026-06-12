---
title: "Synaptic Package Manager Refuses To Load"
date: 2006-09-20
forum: Desktop Environments
---

### Post by bamf on 2006-09-20
Hey,

So I posted this a couple days ago on the newbie forum with no luck, thought I would try again here with all that I have tried.

My problem is when I try to open up synaptic, it prompts me for my password like normal, then after I put it in, it just doesn't load. It acts like I never did anything!

I can still use terminal to get updates and what not... it seems to work fine...

When I type apt-get update I get this...

> kiley@lilbamf:~$ sudo apt-get update
Ign [http://dl.google.com](http://dl.google.com) stable Release.gpg
Hit [http://dl.google.com](http://dl.google.com) stable Release
Get:1 [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release.gpg [189B]
Hit [http://dl.google.com](http://dl.google.com) stable/non-free Packages
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release
Get:2 [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release.gpg [189B]
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release
Get:3 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release.gpg
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release.gpg [189B]
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Get:6 [http://xgl.compiz.info](http://xgl.compiz.info) dapper Release.gpg [189B]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [189B]
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper/main Packages
Ign [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Hit [http://xgl.compiz.info](http://xgl.compiz.info) dapper Release
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Ign [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release
Hit [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Hit [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
Fetched 8B in 2s (3B/s)
Reading package lists... Done

apt-get upgrade I get this...
> Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
linux-image-386 linux-restricted-modules-386
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

I tried to reinstall using aptitude reinstall synaptic...

> kiley@lilbamf:~$ sudo aptitude reinstall synaptic
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages will be REINSTALLED:
synaptic
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 1035kB of archives. After unpacking 0B will be used.
Writing extended state information... Done
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main synaptic 0.57.8ubuntu11 [1035kB]
Fetched 1035kB in 5s (180kB/s)
(Reading database ... 90881 files and directories currently installed.)
Preparing to replace synaptic 0.57.8ubuntu11 (using .../synaptic_0.57.8ubuntu11_i386.deb) ...
Unpacking replacement synaptic ...
Setting up synaptic (0.57.8ubuntu11) ...

I also checked to see if there were errors with it using dpkg ==list synaptic, but I don't think there are any.

> kiley@lilbamf:~$ sudo dpkg --list synaptic
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name Version Description
+++-==============-==============-============================================
ii synaptic 0.57.8ubuntu11 Graphical package manager

Any help or ideas as to why I cant get Synaptic to load up??

---

### Post by PriceChild on 2006-09-20
Could you try launching synaptic from terminal with a:```
gksudo synaptic
```and post the output in the terminal?

---

### Post by bamf on 2006-09-20
when I type gksudo synaptic in terminal it does the same thing as clicking on the icon... asks for password then doesnt load.

---

### Post by bamf on 2006-09-20
Ok, I tried using the debug function and I think I found the problem... no clue how to fix it though!

> kiley@lilbamf:~$ gksudo synaptic -d
xauth: /tmp/libgksu1.2-PeoZxw/.Xauthority
cmd[0]: /usr/bin/sudo
cmd[1]: -H
cmd[2]: -S
cmd[3]: -p
cmd[4]: GNOME_SUDO_PASS
cmd[5]: -u
cmd[6]: root
cmd[7]: --
cmd[8]: synaptic
buffer: -synaptic: error -
No password prompt found; we'll assume we don't need a password.
synaptic: error while loading shared libraries: libvte.so.4: cannot open shared object file: No such file or directory
xauth: /tmp/libgksu1.2-PeoZxw/.Xauthority
xauth_env: /home/kiley/.Xauthority
dir: /tmp/libgksu1.2-PeoZxw


---

### Post by bamf on 2006-09-20
Ok, Im dumb... I search the forums for libvte.so.4 and Im retarded...

typed > sudo ln -s /usr/lib/libvte.so.9 /usr/lib/libvte.so.4

that got it working.

---

