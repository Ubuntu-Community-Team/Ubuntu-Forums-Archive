---
title: "problem install openboard in ubuntu 16.04"
date: 2018-11-06
forum: Education &amp; Science
---

### Post by dimzev on 2018-11-06
i download openboard from [http://openboard.ch/download.en.html](http://openboard.ch/download.en.html) fron ubuntu 16.04
then in terminal write " sudo dpkg -i openboard_ubuntu_16.04_1.4.1_amd64.deb"
and take :[INDENT]sudo dpkg -i openboard_ubuntu_16.04_1.4.1_amd64.deb
Selecting previously unselected package openboard.
(Reading database ... 191101 files and directories currently installed.)
Preparing to unpack openboard_ubuntu_16.04_1.4.1_amd64.deb ...
Unpacking openboard (1.4.1) ...
dpkg: dependency problems prevent configuration of openboard:
 openboard depends on libavformat-ffmpeg56 (>= 7:2.8.14); however:
  Package libavformat-ffmpeg56 is not installed.
 openboard depends on libavcodec-ffmpeg56 (>= 7:2.8.14) | libavcodec-ffmpeg-extra56 (>= 7:2.8.14); however:
  Package libavcodec-ffmpeg56 is not installed.
  Package libavcodec-ffmpeg-extra56 is not installed.
 openboard depends on libswresample-ffmpeg1 (>= 7:2.8.14); however:
  Package libswresample-ffmpeg1 is not installed.
 openboard depends on libswscale-ffmpeg3 (>= 7:2.8.14); however:
  Package libswscale-ffmpeg3 is not installed.
 openboard depends on libavutil-ffmpeg54 (>= 7:2.8.14); however:
  Package libavutil-ffmpeg54 is not installed.
 openboard depends on libqt5multimediawidgets5 (>= 5.5.1); however:
  Package libqt5multimediawidgets5 is not installed.
 openboard depends on libqt5script5 (>= 5.5.1); however:
  Package libqt5script5 is not installed.
 openboard depends on libstdc++6 (>= 5.4.0); however:
  Version of libstdc++6:a
dpkg: error processing package openboard (--install):
 dependency problems - leaving unconfigured
Processing triggers for gnome-menus (3.13.3-6ubuntu3) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160415-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.59ubuntu1) ...
Errors were encountered while processing:
 openboard 
[/INDENT]
then i try install[INDENT]sudo apt-get install libavcodec-ffmpeg56
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libavcodec-ffmpeg56 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libavcodec-ffmpeg56' has no installation candidate
[/INDENT]
what must i do ?
please help me

** **i have install ubuntu 16.04 in usb persistence **

---

