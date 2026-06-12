---
title: "Help! Command line installation removed lots of libraries!"
date: 2009-05-06
forum: General Help
---

### Post by ubu-for on 2009-05-06
I've followed this [hint]('http://chrisjohnston.org/2009/re-enable-ctrl-alt-backspace-904#comments') to enable "Ctrl-Alt-Backspace" but the command also removed "libboost-date-time1.34.1" "libboost-thread1.34.1" "libcpufreq0" "libdvdread3" and maybe 10 other libraries.

Is it possible to reinstall the libraries with one single command from "history" like "apt-get reinstall recently removed files"?

It's not my week. :(

P.S. [If someone knows how to change the monitor frequency to 50 Hz, every hint would be appreciated!]('http://ubuntuforums.org/showthread.php?t=1149923')

---

### Post by slakkie on 2009-05-06
You can do a aptitude search $package_name and reinstall them. But most of the times, libs (packages actually) will be removed if there are no dependencies and the package itself was not installed by you (but because of a dependency with another package).

What you could do, in order to prevent this from happening is running aptitude -s <command>, this will simulate the action:

```

aptitude -s remove firefox
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  sun-java6-plugin
The following packages have been automatically kept back:
  amarok-xine k3b
The following packages have been kept back:
  amarok
The following packages will be REMOVED:
  firefox
0 packages upgraded, 0 newly installed, 1 to remove and 13 not upgraded.
Need to get 0B of archives. After unpacking 123kB will be freed.
The following packages have unmet dependencies:
  sun-java6-plugin: Depends: firefox but it is not installable or
                             firefox-2 but it is not installable or
                             iceweasel which is a virtual package. or
                             mozilla-firefox which is a virtual package. or
                             iceape-browser but it is not installable or
                             mozilla-browser but it is not installable or
                             epiphany-gecko but it is not installable or
                             epiphany-webkit which is a virtual package. or
                             epiphany-browser but it is not installable or
                             galeon but it is not installable or
                             midbrowser but it is not installable or
                             xulrunner but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
firefox-2 [2.0.0.21~tb.21.308+nobinonly-0ubuntu0.8.04.1 (hardy-updates, hardy-security)]

Score is 41

Accept this solution? [Y/n/q/?] y
The following packages have been automatically kept back:
  amarok-xine k3b
The following NEW packages will be automatically installed:
  firefox-2
The following packages have been kept back:
  amarok
The following NEW packages will be installed:
  firefox-2
The following packages will be REMOVED:
  firefox
0 packages upgraded, 1 newly installed, 1 to remove and 13 not upgraded.
Need to get 9206kB of archives. After unpacking 26.6MB will be used.
Do you want to continue? [Y/n/?] y
Would download/install/remove packages.

```

BTW, if you only removed the packages, you can still see them with dpkg -l | grep -v "^ii" if not mistaken.

---

### Post by ubu-for on 2009-05-06
Thank you very much slakkie for your quick and helpful reply!

Most files were indeed needless because of running Jaunty since Alpha 5, but 3 other files not.

I didn't recognize using "aptitude" instead of "apt-get" because of "copy & paste". Next time I should be more careful.

---

### Post by slakkie on 2009-05-06
apt-get and aptitude can be used both, although some functions are available and not in the other, but for installing/removing/purging it should be ok.

---

