---
title: "gnome-panel doesn't work"
date: 2006-09-25
forum: Desktop Environments
---

### Post by Skootle on 2006-09-25
Hi. I have Kubuntu installed, but decided to try Gnome yesterday. Everything installed fine, but I just booted my computer again right now, and the panels  don't seem to work. They're just completely frozen.

I typed in "top" in my console to see if I could restart gnome-panel but it just reloads and I have the same problem. Also, I noticed that gnome-panel is using up way too many resources. 
```

8166 fabian    25   0 51608  19m  14m R 98.5  1.9  10:44.88 gnome-panel

```

I searched this forum for answers, and found that it would be a good idea to uninstall deskbar applet, but I found out I don't even have it installed.
```

You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  gimp-print: Depends: gimp (>= 2.0.4-1) but it is not going to be installed
  ubuntu-desktop: Depends: deskbar-applet but it is not going to be installed
                  Depends: gimp but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```
Ok, so after that, I typed sudo apt-get -f install: everything seems to be going OK, until I get this error:

```

The following extra packages will be installed:
  gimp gimp-data
Suggested packages:
  libgimp-perl
Recommended packages:
  gimp-svg
The following NEW packages will be installed:
  gimp gimp-data
0 upgraded, 2 newly installed, 0 to remove and 24 not upgraded.
200 not fully installed or removed.
Need to get 0B/4871kB of archives.
After unpacking 28.6MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 177535 files and directories currently installed.)
Unpacking gimp-data (from .../gimp-data_2.2.11-1ubuntu3.1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/gimp-data_2.2.11-1ubuntu3.1_all.deb (--unpack):
 trying to overwrite `/usr/share/applications/gimp-2.2.desktop', which is also in package gimpshop
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking gimp (from .../gimp_2.2.11-1ubuntu3.1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/gimp_2.2.11-1ubuntu3.1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/gimp/2.0/environ/default.env', which is also in package gimpshop
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/gimp-data_2.2.11-1ubuntu3.1_all.deb
 /var/cache/apt/archives/gimp_2.2.11-1ubuntu3.1_i386.deb
**[COLOR="Red"]E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]**

Do you guys have any ideas on how to fix this? Thanks. :)

```

---

### Post by ayoli on 2006-09-25
> dpkg: error processing /var/cache/apt/archives/gimp_2.2.11-1ubuntu3.1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/gimp/2.0/environ/default.env', which is also in package gimpshop
try to uninstall gimpshop, then do:
```
sudo dpkg --configure -a
```

for the panel, try:
```
sudo killall gnome-panel
```
that restarts gnome-panel

---

### Post by cptnapalm on 2006-09-25
200!?!?!?!!??

You have 200 packages which are not fully installed or removed?!?!  Wow.

Insofar as installing a new DE, I had all kinds of problems when I installed KDE when I was using regular old Ubuntu.

---

### Post by Skootle on 2006-09-26
Thanks, Ayoli, now Gnome works pretty well. Although Cptnapalm is right, it is giving me some other problems. I'll probably just reformat and install Ubuntu.

Thanks, though. :)

---

