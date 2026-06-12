---
title: "Your method for finding pacakge dependencies?"
date: 2009-06-24
forum: General Help
---

### Post by leaferz on 2009-06-24
What method(s) do you use to find package dependences after downloading a package?

I often find myself using apt/synaptic to download packages but the repos are always a few versions behind (at least). Countless times I've spent hours finding package dependencies which lead to more dependencies, etc. Even worse are dependencies which are eventually found within larger packages which also take up large chunks of time. 

Any ideas would be appreciated. :D

---

### Post by t0p on 2009-06-24
If you're talking about downloading a .deb package, I usually do this:

```
dpkg -i somepackage.deb
```

If this generates a message about unmet dependencies, I follow up with

```
sudo apt-get -f install
```

That will download and install whatever dependencies are needed.

If you're talking about compiling source code, I follow [this guide]("https://help.ubuntu.com/community/CompilingEasyHowTo").

---

### Post by leaferz on 2009-06-24
> **t0p said:**
> If you're talking about downloading a .deb package, I usually do this:

```
dpkg -i somepackage.deb
```

If this generates a message about unmet dependencies, I follow up with

```
sudo apt-get -f install
```

That will download and install whatever dependencies are needed.

If you're talking about compiling source code, I follow [this guide]("https://help.ubuntu.com/community/CompilingEasyHowTo").

Thx for the quick response t0p. Never used the -f option with apt. 

Excellent tutorial on tars. I've only had success with them when my system meets the criteria or if the dependency list isn't too massive. 

I'll give both methods a try on some of the software I've had difficultly with. 

Thx

---

### Post by leaferz on 2009-06-24
> **t0p said:**
> If you're talking about downloading a .deb package, I usually do this:

```
dpkg -i somepackage.deb
```

If this generates a message about unmet dependencies, I follow up with

```
sudo apt-get -f install
```

That will download and install whatever dependencies are needed.


Just gave your method a try and it doesn't seem to be functioning properly. Here's the output from trying to install avidemux2:

> 
**_Attempt#1_**

[COLOR="Blue"]**$ sudo dpkg -i avidemux_2.4.4-0.3_i386.deb **[/COLOR]
Selecting previously deselected package avidemux.
(Reading database ... 129046 files and directories currently installed.)
Unpacking avidemux (from avidemux_2.4.4-0.3_i386.deb) ...
dpkg: dependency problems prevent configuration of avidemux:
 avidemux depends on libamrnb3; however:
  Package libamrnb3 is not installed.
 avidemux depends on libartsc0 (>= 1.5.9); however:
  Package libartsc0 is not installed.
 avidemux depends on libfaac0 (>= 1.28); however:
  Version of libfaac0 on system is 1.26-0.1ubuntu2.
 avidemux depends on libmp3lame0 (>= 3.98.2); however:
  Version of libmp3lame0 on system is 3.98-0.0.
 avidemux depends on libx264-67 (>= 1:0.svn20090516); however:
  Package libx264-67 is not installed.
 avidemux depends on avidemux-common; however:
  Package avidemux-common is not installed.
dpkg: error processing avidemux (--install):
 dependency problems - leaving unconfigured
Processing triggers for menu ...
Processing triggers for man-db ...
Errors were encountered while processing:
 avidemux

[COLOR="Blue"]**$ sudo apt-get install -f**[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  avidemux
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 8249kB disk space will be freed.
Do you want to continue [Y/n]? 

For some reason it tried to remove the file rather then satisfy its dependencies.

I then attempted to dpkg all four files:
> 
**_Attempt#2_**

**[COLOR="Blue"]$ ls[/COLOR]**
avidemux_2.4.4-0.3_i386.deb      avidemux-common_2.4.4-0.3_all.deb
avidemux-cli_2.4.4-0.3_i386.deb  avidemux-qt_2.4.4-0.3_i386.deb

**[COLOR="Blue"]$ sudo dpkg -i avidemux* [/COLOR]**
(Reading database ... 129056 files and directories currently installed.)
Preparing to replace avidemux 1:2.4.4-0.3 (using avidemux_2.4.4-0.3_i386.deb) ...
Unpacking replacement avidemux ...
Selecting previously deselected package avidemux-cli.
Unpacking avidemux-cli (from avidemux-cli_2.4.4-0.3_i386.deb) ...
Selecting previously deselected package avidemux-common.
Unpacking avidemux-common (from avidemux-common_2.4.4-0.3_all.deb) ...
Selecting previously deselected package avidemux-qt.
Unpacking avidemux-qt (from avidemux-qt_2.4.4-0.3_i386.deb) ...
dpkg: dependency problems prevent configuration of avidemux:
 avidemux depends on libamrnb3; however:
  Package libamrnb3 is not installed.
 avidemux depends on libartsc0 (>= 1.5.9); however:
  Package libartsc0 is not installed.
 avidemux depends on libfaac0 (>= 1.28); however:
  Version of libfaac0 on system is 1.26-0.1ubuntu2.
 avidemux depends on libmp3lame0 (>= 3.98.2); however:
  Version of libmp3lame0 on system is 3.98-0.0.
 avidemux depends on libx264-67 (>= 1:0.svn20090516); however:
  Package libx264-67 is not installed.
dpkg: error processing avidemux (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of avidemux-cli:
 avidemux-cli depends on libamrnb3; however:
  Package libamrnb3 is not installed.
 avidemux-cli depends on libartsc0 (>= 1.5.9); however:
  Package libartsc0 is not installed.
 avidemux-cli depends on libfaac0 (>= 1.28); however:
  Version of libfaac0 on system is 1.26-0.1ubuntu2.
 avidemux-cli depends on libmp3lame0 (>= 3.98.2); however:
  Version of libmp3lame0 on system is 3.98-0.0.
 avidemux-cli depends on libx264-67 (>= 1:0.svn20090516); however:
  Package libx264-67 is not installed.
dpkg: error processing avidemux-cli (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of avidemux-qt:
 avidemux-qt depends on libamrnb3; however:
  Package libamrnb3 is not installed.
 avidemux-qt depends on libartsc0 (>= 1.5.9); however:
  Package libartsc0 is not installed.
 avidemux-qt depends on libfaac0 (>= 1.28); however:
  Version of libfaac0 on system is 1.26-0.1ubuntu2.
 avidemux-qt depends on libmp3lame0 (>= 3.98.2); however:
  Version of libmp3lame0 on system is 3.98-0.0.
 avidemux-qt depends on libqtcore4 (>= 4.5.1); however:
  Version of libqtcore4 on system is 4.5.0-0ubuntu4.1.
 avidemux-qt depends on libqtgui4 (>= 4.5.1); however:
  Version of libqtgui4 on system is 4.5.0-0ubuntu4.1.
 avidemux-qt depends on libx264-67 (>= 1:0.svn20090516); however:
  Package libx264-67 is not installed.
dpkg: error processing avidemux-qt (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of avidemux-common:
 avidemux-common depends on avidemux; however:
  Package avidemux is not configured yet.
  Package avidemux-qt which provides avidemux is not configured yet.
  Package avidemux-cli which provides avidemux is not configured yet.
dpkg: error processing avidemux-common (--install):
 dependency problems - leaving unconfigured
Processing triggers for menu ...
Processing triggers for man-db ...
Errors were encountered while processing:
 avidemux
 avidemux-cli
 avidemux-qt
 avidemux-common

**[COLOR="Blue"]$ sudo apt-get install -f[/COLOR]**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  avidemux avidemux-cli avidemux-common avidemux-qt
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 25.9MB disk space will be freed.
Do you want to continue [Y/n]? 

Same result. 

Is there something I'm doing wrong here?

This is more of a learning experience then a requirement because I could use their repo or the available tar file.

---

### Post by cariboo on 2009-06-24
If you want bleeding end packages, Ubuntu is really not the distribution for you. The way Ubuntu works, is it takes packages from Debian unstable, for instance Karmic Koala's Debian import freeze is June 25/09. Essentially there won't be any new versions entered after that date. If a new version of a package is released after the freeze, we have to wait for the next release to be able to take advantage of it.

To answer your question, if I need to find package dependencies I usually use synaptic, just search for the package in question, then highlight it and click the properties button, then click the dependencies tab.

---

### Post by leaferz on 2009-06-24
> **cariboo907 said:**
> If you want bleeding end packages, Ubuntu is really not the distribution for you. The way Ubuntu works, is it takes packages from Debian unstable, for instance Karmic Koala's Debian import freeze is June 25/09. Essentially there won't be any new versions entered after that date. If a new version of a package is released after the freeze, we have to wait for the next release to be able to take advantage of it.

To answer your question, if I need to find package dependencies I usually use synaptic, just search for the package in question, then highlight it and click the properties button, then click the dependencies tab.

How do you go about finding dependencies located within other packages?

Many times I run across tarballs which give you the list of dependencies but often I'm not able to find that exact name within the repositories. I usually notice this when I'm searching around for library files.

---

