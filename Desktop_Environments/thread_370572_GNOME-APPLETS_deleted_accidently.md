---
title: "GNOME-APPLETS deleted accidently"
date: 2007-02-25
forum: Desktop Environments
---

### Post by K-a-M-u-Z-u on 2007-02-25
hi.
i use ubuntu edgy on a IBM thinkpad R40 for a while.
i accidently deleted "gnome-applets" directory while trying to free-up disk space (went to ZERO).
when i rebooter and ubuntu started i got the messege:
> The panel encountered a problem while loading "OAFIID:GNOME_CPUFreqApplet".
and two options:
> do you want to delete the applet from your configuration?
so i thought try to install it again with the code:
```
sudo apt-get update
```
then:
> apt-get -f install
then:
```
sudo apt-get install gnome-applets
and i got:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gnome-applets: Depends: libdbus-1-1 (>= 0.36.2) but it is not going to be installed
                 Depends: libdbus-glib-1-1 (>= 0.36.2) but it is not going to be installed
                 Depends: libnotify0 but it is not going to be installed
E: Broken packages
so i try:
[CODE] sudo aptitude reinstall gnome-applets 

```
got:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information     
Initializing package states... Done
Building tag database... Done     
gnome-applets is not currently installed, so it will not be reinstalled.
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used. 

so i try:
```
sudo aptitude install gnome-applets 
```
got:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information     
Initializing package states... Done
Building tag database... Done     
The following packages are BROKEN:
  dbus libxklavier11
The following NEW packages will be automatically installed:
  gnome-applets-data gstreamer0.8-alsa imagemagick libdbus-1-1
  libdbus-glib-1-1 libgail17 libgstreamer-plugins0.8-0 libgstreamer0.8-0
  libgtop2-5 libgucharmap4 libmagick6 libnotify0 libxklavier10
The following NEW packages will be installed:
  gnome-applets gnome-applets-data gstreamer0.8-alsa imagemagick
  libdbus-1-1 libdbus-glib-1-1 libgail17 libgstreamer-plugins0.8-0
  libgstreamer0.8-0 libgtop2-5 libgucharmap4 libmagick6 libnotify0
  libxklavier10
0 packages upgraded, 14 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.6MB of archives. After unpacking 52.0MB will be used.
The following packages have unmet dependencies:
  dbus: Conflicts: libdbus-1-1 but 0.36.2-0ubuntu7.1 is to be installed.
  libxklavier11: Conflicts: libxklavier10 but 2.0-0.2ubuntu2 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
gnome-applets [Not Installed]
gnome-applets-data [Not Installed]
libdbus-1-1 [Not Installed]
libdbus-glib-1-1 [Not Installed]
libnotify0 [Not Installed]
libxklavier10 [Not Installed]

Score is 44

Accept this solution? [Y/n/q/?] 

how can i fix this?
is there any way to reinstall ubuntu without loosing data?(i changed so much until now and it will be a disaster to reinstall it).
is there a way just to copy the DIRECTORY gnome-applates(the one that i deleted accidently?).
thanks.

[color=red]**Please dont delete my post because i'm not sure where to put it(and someone already deleted it from general support)**[/color]

---

### Post by K-a-M-u-Z-u on 2007-02-26
up?
:confused:

---

