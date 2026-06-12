---
title: "Brother printer problem"
date: 2008-12-05
forum: General Help
---

### Post by alex_sleiborg on 2008-12-05
Hey

I'm trying to install a brother MFC-9420CN. I've downloaded the drivers from brother website. But i can't install the mfc9420cncups-package. And now i get this error

sudo apt-get -f install

The package mfc9420cncups must be reinstalled, can't find any archive


What do i do know?

---

### Post by plucky on 2008-12-05
You need to remove that package using ```
sudo apt-get remove <name of package>
```

Then open Synaptic and search for **mfc9420cn** and install the cupswrapper and LPR drivers.

Once that is installed,open **System > Administration > Printing** and install your printer.


Good Luck

---

### Post by alex_sleiborg on 2008-12-05
That was the first thing i tried, but i'm not able to do that. I't only says it need to be reinstalled, and it can't find the package.??? I've installed it on my other kubuntu machine with no problem at all

---

### Post by plucky on 2008-12-05
What command did you use to install the .deb file in the first place?

Did you satisfy the pre-requisites as specified on the Brother website?
Did the LPR driver install correctly?
Can you open Synaptic Package manager?

---

### Post by jim.madl on 2011-06-17
I have the same exact issue.

the package for me was installed after I ran through what I thought were all the pre-requiites by downloading and running the deb file downloaded from the brother site and opened from the Synaptic package manager .

I have tried to uninstall it using sudo apt-get install -f.  tried apt-get remove -f mfc9420cncups

but  continue to get the same error message  

and now I can not install anything else

---

### Post by jim.madl on 2011-06-17
dpkg -l mfc9420cncups dispdpkg -l mfc9420cncups
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                    Version                 Description
+++-=======================-=======================-==============================================================
pHR mfc9420cncups           1.0.0-1                 Brother CUPS color Printer Definitions
lays the following

Also attempted to re-install with the command
dpkg --install mfc9420cncups-1.0.0-1.debian.i386.deb

that produces the following error
(Reading database ... 114418 files and directories currently installed.)
Preparing to replace mfc9420cncups 1.0.0-1 (using mfc9420cncups-1.0.0-1.debian.i386.deb) ...
Unpacking replacement mfc9420cncups ...
start: Unknown job: cupsys
dpkg: warning: subprocess old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
start: Unknown job: cupsys
dpkg: error processing mfc9420cncups-1.0.0-1.debian.i386.deb (--install):
 subprocess new post-removal script returned error exit status 1
start: Unknown job: cupsys
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 1
Errors were encountered while processing:
 mfc9420cncups-1.0.0-1.debian.i386.deb

The cupsys was part of the prerequisite instructions and it existed as a symbolic link 

I tried changing it to the same link as the cups file and that did not help either

I even went so far as to try to use force options and not luck with them either

would like to upgrade the system but this will not happen unless this issue is resolved may have to re-install

---

