---
title: "kubuntu 14.04 dual monitor settings not saved"
date: 2015-11-07
forum: Desktop Environments
---

### Post by gobo7 on 2015-11-07
trying to do initial install of kubuntu 14.04 on a machine with an
ati fireMV 2250 (RV516) and two monitors.  

the issue is that after a reboot, it only activates the monitor on DVI-1.
DVI-0 is detected and when manually enabled in Display Configuration it 
will work. but the settings are not restored upon reboot.

i've tested with updates to xorg xserver and kde-baseapps, all with no
change.  the xorg.o.log file does not show any file related errors. 
disabled kscreen2, could not tell that change made any difference.

installed and tested fglrx packages from the repos.  once installed, 
only one monitor is detected.  amdconfig claims no adapter is available.

all of the various tests have been done on fresh, clean installs.  the only
added application is muon.

in searching for this condition, the only real result for 14.04 was an issue
related to Unity and its xml config file.  so i've struck out.

does anyone have any suggestions?  need to see any logs?


thanks in advance.
gobo

---

