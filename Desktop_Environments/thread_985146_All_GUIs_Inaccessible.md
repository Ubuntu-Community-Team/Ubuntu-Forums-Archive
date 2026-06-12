---
title: "All GUIs Inaccessible"
date: 2008-11-17
forum: Desktop Environments
---

### Post by harlan@bloomenterprises.o on 2008-11-17
Hello,
  I installed Ubuntu 8.10 Server on my laptop, then installed KDE 4.1.  I found I didn't care for 4.1 and wanted to put on KDE 3.5.  So I tried to install KDE 3.5, without first installing KDE 4.1.  Needless to say, KDE is severely hosed up.
  I then tried to install Gnome desktop, not my preferred, but certainly usable.  That didn't work either as I keep getting errors about KDE's problems.

  I have tried to remove KDE several times, using a number of web pages from the net.  Nothing seems to have worked.
  Here are some of the commands I tried:
    aptitude remove kde4
    aptitude remove kde4-core
    aptitude remove kde4-desktop
    aptitude remove kde3
    aptitude remove kde3-core
  This is NOT a complete list, but I can't remember the exact package names.

  Here is the output from the command "aptitude install gdm":
Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
Writing extended state information...
The following packages are BROKEN:
  kcontrol kdebase kicker konqueror kpersonalizer
The following NEW packages will be installed:
  gdm libdmx1{a} ubuntu-gdm-themes{a} ubuntu-sounds{a} zenity{a}
The following packages will be REMOVED:
  akregator{u} kget{u} libjpeg-progs{u} libxklavier12{u} miscfiles{u}
  xscreensaver{u} xscreensaver-data{u} xscreensaver-gl{u}
The following partially installed packages will be configured:
  kde3-core kdebase-runtime kteatime
0 packages upgraded, 5 newly installed, 8 to remove and 101 not upgraded.
Need to get 0B/7562kB of archives. After unpacking 8712kB will be used.
The following packages have unmet dependencies:
  kpersonalizer: Depends: kdebase-data (> 7:3.5.10) but 4:4.1.2-0ubuntu4 is installed and it is kept back.
  kcontrol: Depends: kdebase-data (> 7:3.5.10) but 4:4.1.2-0ubuntu4 is installed and it is kept back.
  kdebase: Depends: kdebase-data (>= 7:3.5.10-0ubuntu1~intrepid4) but 4:4.1.2-0ubuntu4 is installed and it is kept back.
           Depends: kdebase-kio-plugins (>= 7:3.5.10-0ubuntu1~intrepid4) but it is not installable
           Depends: kdesktop (>= 7:3.5.10-0ubuntu1~intrepid4) but it is not installable
           Depends: ksmserver (>= 7:3.5.10-0ubuntu1~intrepid4) but it is not installable
           Depends: ksplash (>= 7:3.5.10-0ubuntu1~intrepid4) but it is not installable
           Depends: ktip (>= 7:3.5.10-0ubuntu1~intrepid4) but it is not installable
           Depends: kwin (>= 7:3.5.10-0ubuntu1~intrepid4) but it is not installable
  kicker: Depends: kdebase-data (> 7:3.5.10) but 4:4.1.2-0ubuntu4 is installed and it is kept back.
  konqueror: Depends: kdebase-kio-plugins (= 7:3.5.10-0ubuntu1~intrepid4) but it is not installable
             Depends: kdesktop (= 7:3.5.10-0ubuntu1~intrepid4) but it is not installable
The following actions will resolve these dependencies:

Remove the following packages:
dolphin
libkonq5
libkonq5-templates

Install the following packages:
cryptsetup [2:1.0.6-6ubuntu2 (intrepid)]
kdebase-kio-plugins [7:3.5.10-0ubuntu1~intrepid4 (<NULL>)]
kdesktop [7:3.5.10-0ubuntu1~intrepid4 (<NULL>)]
ksmserver [7:3.5.10-0ubuntu1~intrepid4 (<NULL>)]
ksplash [7:3.5.10-0ubuntu1~intrepid4 (<NULL>)]
ktip [7:3.5.10-0ubuntu1~intrepid4 (<NULL>)]
kwin [7:3.5.10-0ubuntu1~intrepid4 (<NULL>)]
pmount [0.9.17-2 (intrepid)]

Upgrade the following packages:
kdebase-data [4:4.1.2-0ubuntu4 (intrepid, now) -> 7:3.5.10-0ubuntu1~intrepid4
(<NULL>)]

Score is 195

Accept this solution? [Y/n/q/?] The following NEW packages will be installed:
  cryptsetup{a} gdm kdebase-kio-plugins{a} kdesktop{a} ksmserver{a}
  ksplash{a} ktip{a} kwin{a} libdmx1{a} pmount{a} ubuntu-gdm-themes{a}
  ubuntu-sounds{a} zenity{a}
The following packages will be REMOVED:
  akregator{u} dolphin{a} kget{u} libjpeg-progs{u} libkonq5{a}
  libkonq5-templates{a} libxklavier12{u} miscfiles{u} xscreensaver{u}
  xscreensaver-data{u} xscreensaver-gl{u}
The following packages will be upgraded:
  kdebase-data
The following partially installed packages will be configured:
  kcontrol kde3-core kdebase kdebase-runtime kicker konqueror kpersonalizer
  kteatime
1 packages upgraded, 13 newly installed, 11 to remove and 100 not upgraded.
Need to get 0B/22.3MB of archives. After unpacking 34.8MB will be used.
Do you want to continue? [Y/n/?] Writing extended state information...
Preconfiguring packages ...
(Reading database ... 159979 files and directories currently installed.)
Preparing to replace kdebase-data 4:4.1.2-0ubuntu4 (using .../kdebase-data_7%3a3.5.10-0ubuntu1~intrepid4_all.deb) ...
Unpacking replacement kdebase-data ...
dpkg: error processing /var/cache/apt/archives/kdebase-data_7%3a3.5.10-0ubuntu1~intrepid4_all.deb (--unpack):
 trying to overwrite `/usr/share/wallpapers/default_blue.jpg', which is also in package kdebase-workspace-wallpapers
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kdebase-data_7%3a3.5.10-0ubuntu1~intrepid4_all.deb
Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
Writing extended state information...

  This output is pretty much the same no matter what aptitude command I try.

  I'm fairly familiar with Linux in general, but not with aptitude in particular.

  How can I clean off all my GUI settings so I can start over?

Thanks,

Harlan...

---

