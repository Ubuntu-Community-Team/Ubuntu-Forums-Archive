---
title: "Skype !!! What's the matter ??"
date: 2006-01-20
forum: Desktop Environments
---

### Post by Seinfeld on 2006-01-20
Hi..
I think I am not the first one complaining about the skype configuration problem, I just want to add that the problem still persists even when installing with the .deb package.. I get the follwing error when I sudo dpkg -i skype_1.2.0.18-1_i386.deb

Selecting previously deselected package skype.
(Reading database ... 57175 files and directories currently installed.)
Unpacking skype (from skype_1.2.0.18-1_i386.deb) ...
dpkg: dependency problems prevent configuration of skype:
 skype depends on libqt3c102-mt (>= 3:3.3.3.2); however:
  Package libqt3c102-mt is not installed.
dpkg: error processing skype (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 skype 

:confused: 

which is the same library missing when installing from the source repository,,
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

Did any one manage to go through the installation successfully?? aaah by the way, apt-get install -f gives the same result.. Here it is

apt-get -f install skype
Reading package lists... Done
Building dependency tree... Done
skype is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  skype: Depends: libqt3c102-mt (>= 3:3.3.3.2) but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Help ?? :???:

---

### Post by darth_vector on 2006-01-20
the deb package on the skyp website is broken. there are good instructions for installing skype here: [http://www.ubuntuguide.org/#skype](http://www.ubuntuguide.org/#skype) and in the wiki.

---

### Post by Seinfeld on 2006-02-07
Check this out.. Try it out. 

[http://forum.skype.com/viewtopic.php?t=30291](http://forum.skype.com/viewtopic.php?t=30291)

The procedure simply "edits" the dependency list file by OR'ing an alternative available library libqt3-mt to the rare/unavailable one
libqt3c102-mt (>= 3:3.3.3.2) | libqt3-mt

BINGO.. It works......\\:D/ 

Thanks

---

