---
title: "Problems installing OpenOffice"
date: 2009-02-27
forum: General Help
---

### Post by kogger on 2009-02-27
My OpenOffice has been having some issues lately, so I tried uninstalling it and re-installing it to see if that could fix the problem, but here's what I get when I try to install it (the errors show up near the bottom):

```
[~/Desktop/CJLZ600LE-CUPS-1.0-1] > sudo apt-get install openoffice.org
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  openoffice.org-base openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-emailmerge
  openoffice.org-filter-binfilter openoffice.org-filter-mobiledev
  openoffice.org-impress openoffice.org-java-common openoffice.org-math
  openoffice.org-officebean openoffice.org-report-builder-bin
  openoffice.org-style-human openoffice.org-writer
  openoffice.org-writer2latex python-uno
Suggested packages:
  openoffice.org-help-2.4 openoffice.org-l10n-2.4 unixodbc
  openoffice.org-hyphenation openoffice.org2-thesaurus openoffice.org-gnome
  openoffice.org-kde openclipart-openoffice.org pstoedit
  gstreamer0.10-plugins-bad libmyodbc odbc-postgresql libsqliteodbc tdsodbc
  mdbtools libmysql-java libpg-java openoffice.org-gcj
  openoffice.org-report-builder openoffice.org-style-industrial
  openoffice.org-style-hicontrast
The following NEW packages will be installed:
  openoffice.org openoffice.org-base openoffice.org-calc
  openoffice.org-common openoffice.org-core openoffice.org-draw
  openoffice.org-emailmerge openoffice.org-filter-binfilter
  openoffice.org-filter-mobiledev openoffice.org-impress
  openoffice.org-java-common openoffice.org-math openoffice.org-officebean
  openoffice.org-report-builder-bin openoffice.org-style-human
  openoffice.org-writer openoffice.org-writer2latex python-uno
0 upgraded, 18 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/63.1MB of archives.
After this operation, 236MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package openoffice.org-style-human.
(Reading database ... 166568 files and directories currently installed.)
Unpacking openoffice.org-style-human (from .../openoffice.org-style-human_1%3a2.4.1-11ubuntu2.1_all.deb) ...
Selecting previously deselected package openoffice.org-common.
Unpacking openoffice.org-common (from .../openoffice.org-common_1%3a2.4.1-11ubuntu2.1_all.deb) ...
Selecting previously deselected package openoffice.org-core.
Unpacking openoffice.org-core (from .../openoffice.org-core_1%3a2.4.1-11ubuntu2.1_i386.deb) ...
Selecting previously deselected package openoffice.org-writer.
Unpacking openoffice.org-writer (from .../openoffice.org-writer_1%3a2.4.1-11ubuntu2.1_i386.deb) ...
Selecting previously deselected package openoffice.org-calc.
Unpacking openoffice.org-calc (from .../openoffice.org-calc_1%3a2.4.1-11ubuntu2.1_i386.deb) ...
Selecting previously deselected package openoffice.org-draw.
Unpacking openoffice.org-draw (from .../openoffice.org-draw_1%3a2.4.1-11ubuntu2.1_i386.deb) ...
Selecting previously deselected package openoffice.org-impress.
Unpacking openoffice.org-impress (from .../openoffice.org-impress_1%3a2.4.1-11ubuntu2.1_i386.deb) ...
Selecting previously deselected package openoffice.org-math.
Unpacking openoffice.org-math (from .../openoffice.org-math_1%3a2.4.1-11ubuntu2.1_i386.deb) ...
Selecting previously deselected package openoffice.org-java-common.
Unpacking openoffice.org-java-common (from .../openoffice.org-java-common_1%3a2.4.1-11ubuntu2.1_all.deb) ...
Selecting previously deselected package openoffice.org-base.
Unpacking openoffice.org-base (from .../openoffice.org-base_1%3a2.4.1-11ubuntu2.1_i386.deb) ...
Selecting previously deselected package openoffice.org-report-builder-bin.
Unpacking openoffice.org-report-builder-bin (from .../openoffice.org-report-builder-bin_1%3a2.4.1-11ubuntu2.1_i386.deb) ...
Selecting previously deselected package openoffice.org-officebean.
Unpacking openoffice.org-officebean (from .../openoffice.org-officebean_1%3a2.4.1-11ubuntu2.1_i386.deb) ...
Selecting previously deselected package openoffice.org-writer2latex.
Unpacking openoffice.org-writer2latex (from .../openoffice.org-writer2latex_0.5-8ubuntu1_all.deb) ...
Selecting previously deselected package openoffice.org-filter-mobiledev.
Unpacking openoffice.org-filter-mobiledev (from .../openoffice.org-filter-mobiledev_1%3a2.4.1-11ubuntu2.1_all.deb) ...
Selecting previously deselected package openoffice.org.
Unpacking openoffice.org (from .../openoffice.org_1%3a2.4.1-11ubuntu2.1_i386.deb) ...
Selecting previously deselected package python-uno.
Unpacking python-uno (from .../python-uno_1%3a2.4.1-11ubuntu2.1_i386.deb) ...
Selecting previously deselected package openoffice.org-emailmerge.
Unpacking openoffice.org-emailmerge (from .../openoffice.org-emailmerge_1%3a2.4.1-11ubuntu2.1_all.deb) ...
Selecting previously deselected package openoffice.org-filter-binfilter.
Unpacking openoffice.org-filter-binfilter (from .../openoffice.org-filter-binfilter_1%3a2.4.1-11ubuntu2.1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for menu ...
Setting up openoffice.org-core (1:2.4.1-11ubuntu2.1) ...
Setting up openoffice.org-style-human (1:2.4.1-11ubuntu2.1) ...
Setting up openoffice.org-writer (1:2.4.1-11ubuntu2.1) ...

Setting up openoffice.org-calc (1:2.4.1-11ubuntu2.1) ...

Setting up openoffice.org-draw (1:2.4.1-11ubuntu2.1) ...

Setting up openoffice.org-impress (1:2.4.1-11ubuntu2.1) ...

Setting up openoffice.org-math (1:2.4.1-11ubuntu2.1) ...

Setting up python-uno (1:2.4.1-11ubuntu2.1) ...

Setting up openoffice.org-emailmerge (1:2.4.1-11ubuntu2.1) ...
Adding extension /usr/lib/openoffice/program/mailmerge.py...pythonloader.Loader ctor
pythonloader.Loader.writeRegistryInfo
pythonloader: interpreting url vnd.sun.star.expand:$UNO_SHARED_PACKAGES_CACHE/uno_packages/mQVO4p_/mailmerge.py
pythonloader: after expansion file:///var/spool/openoffice/uno_packages/cache/uno_packages/mQVO4p_/mailmerge.py
checking for existence of /var/spool/openoffice/uno_packages/cache/uno_packages/mQVO4p_/pythonpath.zip
pythonloader.Loader ctor
pythonloader.Loader.writeRegistryInfo
pythonloader: interpreting url vnd.sun.star.expand:$UNO_SHARED_PACKAGES_CACHE/uno_packages/mQVO4p_/mailmerge.py
pythonloader: after expansion file:///var/spool/openoffice/uno_packages/cache/uno_packages/mQVO4p_/mailmerge.py
pythonloader.Loader.activate
pythonloader: interpreting url vnd.sun.star.expand:$UNO_SHARED_PACKAGES_CACHE/uno_packages/mQVO4p_/mailmerge.py
pythonloader: after expansion file:///var/spool/openoffice/uno_packages/cache/uno_packages/mQVO4p_/mailmerge.py
 done.

Setting up openoffice.org-filter-binfilter (1:2.4.1-11ubuntu2.1) ...

Setting up openoffice.org-common (1:2.4.1-11ubuntu2.1) ...
/var/lib/dpkg/info/openoffice.org-common.postinst: 101: update-openoffice-dicts: not found
dpkg: error processing openoffice.org-common (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of openoffice.org-java-common:
 openoffice.org-java-common depends on openoffice.org-common; however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base:
 openoffice.org-base depends on openoffice.org-java-common (>> 2.2.0-4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-base (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                             No apport report written because the error message indicates its a followup error from a previous failure.
                                                          dpkg: dependency problems prevent configuration of openoffice.org-report-builder-bin:
 openoffice.org-report-builder-bin depends on openoffice.org-base (>= 2.3.0~src680m225); however:
  Package openoffice.org-base is not configured yet.
dpkg: error processing openoffice.org-report-builder-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-officebean:
 openoffice.org-officebean depends on openoffice.org-java-common (>> 2.2.0-4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-officebean (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-writer2latex:
 openoffice.org-writer2latex depends on openoffice.org-java-common (>= 1:2.3.0~oog680m1); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-writer2latex (--configure):
 dependency probleNo apport report written because MaxReports is reached already
   No apport report written because MaxReports is reached already
                                                                 No apport report written because MaxReports is reached already
                                                  No apport report written because MaxReports is reached already
                                   No apport report written because MaxReports is reached already
                    ms - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-filter-mobiledev:
 openoffice.org-filter-mobiledev depends on openoffice.org-java-common (>> 2.2.0-4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-filter-mobiledev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org:
 openoffice.org depends on openoffice.org-base; however:
  Package openoffice.org-base is not configured yet.
 openoffice.org depends on openoffice.org-report-builder-bin; however:
  Package openoffice.org-report-builder-bin is not configured yet.
 openoffice.org depends on openoffice.org-officebean; however:
  Package openoffice.org-officebean is not configured yet.
 openoffice.org depends on openoffice.org-writer2latex; however:
  Package openoffice.org-writer2latex is not configured yet.
 openoffice.org depends on openoffice.org-filter-mobiledev; however:
  Package openoffice.org-filter-mobiledev is not configured yet.
 openoffice.org depends on openoffice.org-java-common (>> 2.2.0-4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org (--configure):
 dependency problems - leaving unconfigured
Processing triggers for menu ...
Errors were encountered while processing:
 openoffice.org-common
 openoffice.org-java-common
 openoffice.org-base
 openoffice.org-report-builder-bin
 openoffice.org-officebean
 openoffice.org-writer2latex
 openoffice.org-filter-mobiledev
 openoffice.org
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Any idea what's going on or how to fix this?

---

### Post by oldos2er on 2009-02-27
Try running 'sudo dpkg --configure -a'

---

### Post by kogger on 2009-02-27
Here's what I got:

```
[~] > sudo dpkg --configure -a
Setting up openoffice.org-common (1:2.4.1-11ubuntu2.1) ...
/var/lib/dpkg/info/openoffice.org-common.postinst: 101: update-openoffice-dicts: not found
dpkg: error processing openoffice.org-common (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of openoffice.org-java-common:
 openoffice.org-java-common depends on openoffice.org-common; however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-officebean:
 openoffice.org-officebean depends on openoffice.org-java-common (>> 2.2.0-4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-officebean (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base:
 openoffice.org-base depends on openoffice.org-java-common (>> 2.2.0-4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-filter-mobiledev:
 openoffice.org-filter-mobiledev depends on openoffice.org-java-common (>> 2.2.0-4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-filter-mobiledev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-writer2latex:
 openoffice.org-writer2latex depends on openoffice.org-java-common (>= 1:2.3.0~oog680m1); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-writer2latex (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-report-builder-bin:
 openoffice.org-report-builder-bin depends on openoffice.org-base (>= 2.3.0~src680m225); however:
  Package openoffice.org-base is not configured yet.
dpkg: error processing openoffice.org-report-builder-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org:
 openoffice.org depends on openoffice.org-base; however:
  Package openoffice.org-base is not configured yet.
 openoffice.org depends on openoffice.org-report-builder-bin; however:
  Package openoffice.org-report-builder-bin is not configured yet.
 openoffice.org depends on openoffice.org-officebean; however:
  Package openoffice.org-officebean is not configured yet.
 openoffice.org depends on openoffice.org-writer2latex; however:
  Package openoffice.org-writer2latex is not configured yet.
 openoffice.org depends on openoffice.org-filter-mobiledev; however:
  Package openoffice.org-filter-mobiledev is not configured yet.
 openoffice.org depends on openoffice.org-java-common (>> 2.2.0-4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 openoffice.org-common
 openoffice.org-java-common
 openoffice.org-officebean
 openoffice.org-base
 openoffice.org-filter-mobiledev
 openoffice.org-writer2latex
 openoffice.org-report-builder-bin
 openoffice.org

```

---

### Post by oldos2er on 2009-02-27
Can you please post the output of this command
```
cat /etc/apt/sources.list
```

---

### Post by kogger on 2009-02-27
cat /etc/apt/sources.list gave me:

```
[~] > cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu hardy-security main restricted
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu hardy-security universe
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports restricted main multiverse universe
# deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main

```

I noticed something near the top...I'm running 8.10, but it says 8.04.

---

### Post by oldos2er on 2009-02-27
As long as those first three lines remain commented out, you'll be fine. You can remove them if you like.

 Try uncommenting the very last line (deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main), then in a terminal run
```
sudo apt-get update && sudo apt-get install openoffice.org
```

---

### Post by kogger on 2009-02-28
Alright, I think it worked. It also updated my openoffice to 3.0, which didn't want to work correctly before either, but so far it looks like everything is fixed.

Thanks. =)

---

### Post by halalkebabhut on 2009-08-22
Hi I'm having problems installing openoffice on my ubuntu studio 9.04 - I tried to run an install via the synaptic package manager and it hung when trying to run a component - now I've been trying to follow the instructions from this link 

[http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml](http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml) 

but when I get to running the update manager it hangs on trying to remove openoffice.org-writer2latex ... 

?

---

### Post by scouser73 on 2009-08-22
**_Openoffice Installation 3.1.0_**

Firstly, go to the OpenOffice website: [http://download.openoffice.org/other.html](http://download.openoffice.org/other.html) and download the **Linux .deb** file.

Once you have done that, extract the .deb file, **OOo_3.1.0_LinuxIntel_install_en-US_deb.tar.gz** then you'll see a file called **OOO310_m11_native_packed-4_en-US.9399**

You can remove the existing version of OpenOffice if you wish with this command: **sudo apt-get remove openoffice*.***

Copy and paste **OOO310_m11_native_packed-4_en-US.9399** onto the desktop then open Terminal and paste this command: **sudo dpkg -i ~/Desktop/OOO310_m11_native_packed-4_en-US.9399/DEBS/*.deb**

Then paste this command: [B]sudo dpkg -i ~/Desktop/OOO310_m11_native_packed-4_en-US.9399/DEBS/desktop-integration/openoffice.org3.1-debian-menus_3.1-9393_all.deb
[/B]
Once you've done that you'll find OpenOffice 3.1.0 in Office.

---

### Post by halalkebabhut on 2009-08-23
okay so when I tried to run **sudo apt-get remove openoffice*.* **it told me to first run **sudo dpkg --configure -a** which i did - no results posted then reran the remove command but it didn't find any office at all. so I ran 
**sudo dpkg -i ~/Desktop/OOO310_m11_native_packed-4_en-US.9399/DEBS/*.deb**
 
but it hangs when it gets to installing the dictionaries. I think this is because of the old version stuck on the system. Actually when I installed my Ubuntu Studio 9.04 all I had was the dictionary (not the rest of office) so perhaps this has something to do with it ?

any suggestions to get rid of office and start again ?

---

