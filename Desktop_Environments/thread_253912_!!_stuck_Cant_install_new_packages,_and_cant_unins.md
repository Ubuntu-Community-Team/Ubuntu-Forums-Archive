---
title: "!! stuck Cant install new packages, and cant uninstall broken ones"
date: 2006-09-09
forum: Desktop Environments
---

### Post by datelus on 2006-09-09
Hello.
Im having some problems with my ubuntu almost every day.Ususaly i fix them by myself, by reading this forum,or others, but today my problem is, that i needed bittorrent, so i tried azureus. at first i used consule, to install that. it also installed some java thing. but not compleatly. So now i cant install any new programs. it usualy displays this:
> datelus@datelus-desktop:~$ sudo apt-get install sox
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  azureus: Depends: libgtk-java but it is not going to be installed
  libgtk-jni: Depends: libgtk-java (= 2.8.4-0ubuntu4) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


i tried apt-get -f install and everything, i even tried synaptic, and cant  remove azureus and them java pakages :( i kind a mar them for complete removal but when i press aply it dosent change a bit. so please help someone. 

-thanks

ps
> datelus@datelus-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libgtk-java
The following NEW packages will be installed:
  libgtk-java
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
12 not fully installed or removed.
Need to get 0B/2144kB of archives.
After unpacking 21.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: parse error, in file `/var/lib/dpkg/available' near line 7294 package `xkeysw-config':
 too many values in file details field `Size' (compared to others)
E: Sub-process /usr/bin/dpkg returned an error code (2)
datelus@datelus-desktop:~$


---

### Post by 454redhawk on 2006-09-09
> **datelus said:**
> Hello.
Im having some problems with my ubuntu almost every day.Ususaly i fix them by myself, by reading this forum,or others, but today my problem is, that i needed bittorrent, so i tried azureus. at first i used consule, to install that. it also installed some java thing. but not compleatly. So now i cant install any new programs. it usualy displays this:


i tried apt-get -f install and everything, i even tried synaptic, and cant  remove azureus and them java pakages :( i kind a mar them for complete removal but when i press aply it dosent change a bit. so please help someone. 

-thanks

ps



Did you install a NON Ubuntu debian package? Do you have broken packages? If so you may be screwed.

Sorry. It happened to me too. Had to reinstall. I hope this is not the case for you.

---

### Post by datelus on 2006-09-09
well i have 2 broken packages. I tried to install azureus when it happened :(
realy, not a chance?

---

### Post by Ramses de Norre on 2006-09-09
Could you post the contents of /var/lib/dpkg/available, in particular the part about xkeysw-config near line 7294.

---

### Post by Junx on 2006-09-09
> **Ramses de Norre said:**
> Could you post the contents of /var/lib/dpkg/available, in particular the part about xkeysw-config near line 7294.
Yeah, do that, we might be able to write a hack that can fix it for you.  I've had problems in the past (usually with Debian Sid, so now I know how to fix them) with postinst scripts and the like, so writing a hack until it gets fixed usually helps.

---

### Post by datelus on 2006-09-10
Thanks, guys that would be great. 
> Package: xkeysw-config
Priority: optional
Section: universe/x11
Installed-Size: 96
Origin: Ubuntu
Maintainer: Dima Barsky <dima@debian.org>
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Architecture: i386
Source: xkeysw
Version: 1.1-1.2ubuntu1
Depends: python (>= 2.4), python (<< 2.5), python-gtk-1.2, python-glade-1.2 (>= 0.6.9), python-xlib
Recommends: xkeysw
Filename: pool/universe/x/xkeysw/xkeysw-config_1.1m1.2ubuntu1_i386.deb
Size: 12278JMD5sum: 442067a6f771bb255d34beac8b7ef289
Description: xkeysw configurator
 A GUI tool to generate and edit the configuration file for xkeysw,
 a keyboard layout switch`for the X Window System.
 .
 See the xkeysw description for more information.


Gues this is it :)

---

### Post by tuxinvader on 2006-09-10
Looks like a newline is missing.

"Size: 12278JMD5sum: 442067a6f771bb255d34beac8b7ef289"

Change that to 

"Size: 12278"
"MD5sum: 442067a6f771bb255d34beac8b7ef289"

Hopefully the J where the new line should have been is the only corruption, but if you say you have a lot of problems installing packages it might not be. Good luck!

---

### Post by datelus on 2006-09-10
just tried that :
sudo apt-get install -f 
> (Reading database ... 74230 files and directories currently installed.)
Unpacking libgtk-java (from .../libgtk-java_2.8.4-0ubuntu4_all.deb) ...
^[OFdpkg: error processing /var/cache/apt/archives/libgtk-java_2.8.4-0ubuntu4_all.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libgtk-java_2.8.4-0ubuntu4_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


..trying to remove 2 broken packages java and szureus..

Ok now it worked! =D> 

..Trying to apt-get install -f again

> datelus@datelus-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
datelus@datelus-desktop:~$



Works fine now! A realy big thanks to you, tuxinvader, and hope this will help to somebody else:cool:

---

### Post by aktiwers on 2006-09-10
Sorry If im hijacking the thread, but it seams to be solved.
Could any of you maybe take a look at my problem? I have a problem simulair to this one, and we just cant fix it.

Please have a look.
[http://ubuntuforums.org/showthread.php?t=252762](http://ubuntuforums.org/showthread.php?t=252762)

Any ideas?

---

### Post by tuxinvader on 2006-09-10
Can you run the following in a temrinal and post the output.

   grep -A5 -B5 openoffice.org-core05 /var/lib/dpkg/available

Cheers

[edit] Where are you getting these packages. They're not in Dapper? :confused:

---

