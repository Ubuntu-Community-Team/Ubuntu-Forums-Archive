---
title: "KDE uninstall/Load Screen/kio-umountwrapper ??"
date: 2008-08-15
forum: Desktop Environments
---

### Post by r0buntu on 2008-08-15
I decided to try out KDE, didnt like it so I removed it by following the directions in this thread-->

[http://ubuntuforums.org/showthread.php?t=874503](http://ubuntuforums.org/showthread.php?t=874503)

sudo aptitude purge kubuntu-kde4-desktop
sudo aptitude purge kdm-kde4
sudo dpkg-reconfigure kdm
sudo aptitude purge ~nkde4

However, when installing i used the command 'sudo apt-get install kubuntu-desktop' (kde3)
so when i uninstalled i did this:
sudo aptitude purge kubuntu-desktop
sudo aptitude purge kdm
sudo dpkg-reconfigure kdm  (said kdm was not installed)
sudo aptitude purge ~nkde 

I had to change /etc/X11/default-display-manager back to gdm, because it prompted for a default and i selected kdm.

Gnome works fine again, however i want to get rid of the kubuntu load screen and go back to the original ubuntu screen.
I tried following the directions in this thread:
[http://ubuntuforums.org/showthread.php?t=885588](http://ubuntuforums.org/showthread.php?t=885588)

sudo apt-get install startupmanager

gives me this error: 

robbie@latituded410:~$ sudo apt-get install startupmanager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libpythonize0 libsearchclient0 libmimelib1c2a libflac++6 libfftw3-3
  python-dev libexiv2-2 python2.5-dev pykdeextensions cryptsetup libgmp3c2
  perl-suid libept0 libksba8 libxapian15 poster libtunepimp5 libifp4
  libdbus-qt-1-1c2 rdiff-backup ksysguardd libstrigihtmlgui0 psutils
  libpoppler-qt2 libjpeg-progs pinentry-qt librsync1 libnjb5 libofa0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  imagemagick menu
The following packages will be REMOVED:
  kio-umountwrapper
The following NEW packages will be installed:
  imagemagick menu startupmanager
0 upgraded, 3 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/1952kB of archives.
After this operation, 7475kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 172381 files and directories currently installed.)
Removing kio-umountwrapper ...
Removing `diversion of /usr/share/apps/konqueror/servicemenus/media_safelyremove.desktop to /usr/share/apps/konqueror/servicemenus/media_safelyremove.desktop.distrib by kio-umountwrapper'
dpkg-divert: error checking `/usr/share/apps/konqueror/servicemenus/media_safelyremove.desktop': No such file or directory
dpkg: error processing kio-umountwrapper (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 kio-umountwrapper
E: Sub-process /usr/bin/dpkg returned an error code (1)
robbie@latituded410:~$ 

Can anyone point me in the right direction here? Maybe aptitude purge kdm was a mistake?

---

