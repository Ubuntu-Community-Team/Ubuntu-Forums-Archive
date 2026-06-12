---
title: "xfce4 packages broken?"
date: 2005-06-18
forum: Desktop Environments
---

### Post by James_Ward on 2005-06-18
I followed the instructions on [http://www.os-works.com/view/debian](http://www.os-works.com/view/debian) and I get this when trying to add their xfce4 packages:

jeward@fiva:/etc/apt$ sudo apt-get install -t testing xfld-desktop
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  xfld-desktop: Depends: xfce4 (>= 4.2.1.1-2) but it is not going to be installed
E: Broken packages

Is it me, or are their packages really broken?

---

### Post by Xian on 2005-06-18
[QUOTE=James_Ward]I followed the instructions on [http://www.os-works.com/view/debian](http://www.os-works.com/view/debian) and I get this when trying to add their xfce4 packages:

jeward@fiva:/etc/apt$ sudo apt-get install -t testing xfld-desktop[/QUOTE]
That is referencing a "testing" version repo for Debian Linux.
Ubuntu does not share that repository.

---

### Post by Xian on 2005-06-18
Just out of curiosity I went ahead and added the repos below to the sources.list, then opened Synaptic and marked 'xfld-desktop' to be installed. Synaptic pulled all the needed deps and gave the okay to install (save a warning about a missing file signature -- no biggie), so the packages should process fine on you system. However, I am not aware of any info that states these .deb files are appropriate for Ubuntu so you might want to consider this before you commit the additional software.

```
deb http://www.os-works.com/debian testing main
deb-src http://www.os-works.com/debian testing main
```

```
$ sudo apt-get update
$ sudo apt-get install xfld-desktop
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  a2ps emacsen-common gtk2-engines-xfce libdbh1.0-1 libexo0.3-0 libxfce4mcs-client-2 libxfce4mcs-manager-2 libxfce4util-1
  libxfcegui4-3 mousepad rox-filer xfcalendar xfce4 xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin
  xfce4-cpugraph-plugin xfce4-datetime-plugin xfce4-diskperf-plugin xfce4-fsguard-plugin xfce4-genmon-plugin
  xfce4-icon-theme xfce4-iconbox xfce4-mcs-manager xfce4-mcs-plugins xfce4-minicmd-plugin xfce4-mixer xfce4-mixer-lib-alsa
  xfce4-netload-plugin xfce4-notes-plugin xfce4-panel xfce4-panel-menu-plugin xfce4-session xfce4-showdesktop-plugin
  xfce4-systemload-plugin xfce4-systray xfce4-taskbar-plugin xfce4-toys xfce4-trigger-launcher xfce4-utils
  xfce4-wavelan-plugin xfce4-weather-plugin xfce4-windowlist-plugin xfce4-xkb-plugin xfdesktop4 xffm4 xfmedia xfprint4
  xfwm4 xfwm4-themes xterminal
Suggested packages:
  emacs21-nox emacsen groff gv html2ps tetex-bin t1-cyrillic xine-ui xfce4-theme-brushedchrome
Recommended packages:
  wdiff gqview
The following NEW packages will be installed:
  a2ps emacsen-common gtk2-engines-xfce libdbh1.0-1 libexo0.3-0 libxfce4mcs-client-2 libxfce4mcs-manager-2 libxfce4util-1
  libxfcegui4-3 mousepad rox-filer xfcalendar xfce4 xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin
  xfce4-cpugraph-plugin xfce4-datetime-plugin xfce4-diskperf-plugin xfce4-fsguard-plugin xfce4-genmon-plugin
  xfce4-icon-theme xfce4-iconbox xfce4-mcs-manager xfce4-mcs-plugins xfce4-minicmd-plugin xfce4-mixer xfce4-mixer-lib-alsa
  xfce4-netload-plugin xfce4-notes-plugin xfce4-panel xfce4-panel-menu-plugin xfce4-session xfce4-showdesktop-plugin
  xfce4-systemload-plugin xfce4-systray xfce4-taskbar-plugin xfce4-toys xfce4-trigger-launcher xfce4-utils
  xfce4-wavelan-plugin xfce4-weather-plugin xfce4-windowlist-plugin xfce4-xkb-plugin xfdesktop4 xffm4 xfld-desktop xfmedia
  xfprint4 xfwm4 xfwm4-themes xterminal
0 upgraded, 52 newly installed, 0 to remove and 1 not upgraded.
Need to get 14.5MB of archives.
After unpacking 63.7MB of additional disk space will be used.
Do you want to continue [Y/n]?
```

---

