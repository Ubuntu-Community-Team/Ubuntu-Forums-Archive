---
title: "fgrun install script"
date: 2011-01-20
forum: Gaming &amp; Leisure
---

### Post by ubudog on 2011-01-20
Hi there community!  I would like to share a small script I made for the Ubuntu gaming crowd.  The script downloads everything needed to run fgrun (the FlightGear launcher), and puts the user at a point where typing fgrun in a terminal starts it.  So basically an install script.  :p  Anyway, to run, just type:

```
./downloadinstallfgrun.sh
```

And then after it's done, to open fgrun...

```
fgrun
```

That will prompt for a password for apt, to install the necessary packages.  The script is open-source, and anyone can do whatever they want with it.  If you find any errors, or need help on using it, post a reply here, and I would be glad to help.  Hope this helps people!  

PS: After installing, you can change the FlightGear menu item command from "fgfs" to "fgrun", and upon clicking, it will open fgrun.

It is attached.
Backup of the script at my site: [http://ubudog.homelinux.net/scripts/](http://ubudog.homelinux.net/scripts/)
UPDATE (Sun, Jun 26, 2011) - Updates the license.  Now GNU GPLV3.

---

### Post by meeps on 2011-01-26
Thank you! Works great! It does redownload the SimGear packages if run multiple times, but that's ok. Thanks though!

---

### Post by ubudog on 2011-01-27
> **meeps said:**
> Thank you! Works great! It does redownload the SimGear packages if run multiple times, but that's ok. Thanks though!

Thanks for downloading!  I believe the cleanup feature removes all the SimGear.tar.gz's, but I'm not sure.  If you want to change something, and want it here, email me it, and I'll upload the changed version!

---

### Post by JayKav on 2011-02-05
Sorry, didn't work for me. I'm running 10.10 on AMD 64

Reading package lists... Done
Building dependency tree       
Reading state information... Done
zlib1g is already the newest version.
zlib1g-dev is already the newest version.
zlib1g-dev set to manually installed.
libalut0 is already the newest version.
libalut0 set to manually installed.
libopenal1 is already the newest version.
libopenal1 set to manually installed.
libplib1 is already the newest version.
libplib1 set to manually installed.
The following packages were automatically installed and are no longer required:
  libproj0 libsvga1 mplayer libogdi3.2 libcoin60 unixodbc libgdal1-1.6.0 libmp3lame0 mplayer-skins
  libxerces-c28 libopenthreads13 libhdf5-serial-1.8.4 libgeos-c1 proj-data liblzo2-2 proj-bin simgear1.9.1
  libgeos-3.2.0 libxvidcore4 libvdpau1 libpq5 libgfortran3 libhdf4-0-alt libopenscenegraph65 libnetcdf6
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  freeglut3-dev
Suggested packages:
  fltk1.1-doc fluid
The following NEW packages will be installed:
  freeglut3-dev libalut-dev libfltk1.1 libfltk1.1-dev libopenal-dev libplib-dev
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,317kB of archives.
After this operation, 9,056kB of additional disk space will be used.
Get:1 [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick/main freeglut3-dev amd64 2.6.0-0ubuntu2 [214kB]
Get:2 [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick/universe libopenal-dev amd64 1:1.12.854-2 [20.5kB]
Get:3 [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick/universe libalut-dev amd64 1.1.0-2 [38.8kB]
Get:4 [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick/main libfltk1.1 amd64 1.1.10-2 [464kB]
Get:5 [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick/main libfltk1.1-dev amd64 1.1.10-2 [645kB]
Get:6 [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick/universe libplib-dev amd64 1.8.5-5 [935kB]
Fetched 2,317kB in 2s (940kB/s)    
Preconfiguring packages ...
Selecting previously deselected package freeglut3-dev.
(Reading database ... 206895 files and directories currently installed.)
Unpacking freeglut3-dev (from .../freeglut3-dev_2.6.0-0ubuntu2_amd64.deb) ...
Selecting previously deselected package libopenal-dev.
Unpacking libopenal-dev (from .../libopenal-dev_1%3a1.12.854-2_amd64.deb) ...
Selecting previously deselected package libalut-dev.
Unpacking libalut-dev (from .../libalut-dev_1.1.0-2_amd64.deb) ...
Selecting previously deselected package libfltk1.1.
Unpacking libfltk1.1 (from .../libfltk1.1_1.1.10-2_amd64.deb) ...
Selecting previously deselected package libfltk1.1-dev.
Unpacking libfltk1.1-dev (from .../libfltk1.1-dev_1.1.10-2_amd64.deb) ...
Selecting previously deselected package libplib-dev.
Unpacking libplib-dev (from .../libplib-dev_1.8.5-5_amd64.deb) ...
Processing triggers for man-db ...
Setting up freeglut3-dev (2.6.0-0ubuntu2) ...
Setting up libopenal-dev (1:1.12.854-2) ...
Setting up libalut-dev (1.1.0-2) ...
Setting up libfltk1.1 (1.1.10-2) ...
Setting up libfltk1.1-dev (1.1.10-2) ...
Setting up libplib-dev (1.8.5-5) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
--2011-02-05 12:35:50--  [http://sourceforge.net/projects/fgrun/files/fgrun/1.5.2/fgrun-1.5.2.tar.gz/download](http://sourceforge.net/projects/fgrun/files/fgrun/1.5.2/fgrun-1.5.2.tar.gz/download)
Resolving sourceforge.net... 216.34.181.60
Connecting to sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/project/fgrun/fgrun/1.5.2/fgrun-1.5.2.tar.gz?r=&ts=1296902151&use_mirror=puzzle](http://downloads.sourceforge.net/project/fgrun/fgrun/1.5.2/fgrun-1.5.2.tar.gz?r=&ts=1296902151&use_mirror=puzzle) [following]
--2011-02-05 12:35:51--  [http://downloads.sourceforge.net/project/fgrun/fgrun/1.5.2/fgrun-1.5.2.tar.gz?r=&ts=1296902151&use_mirror=puzzle](http://downloads.sourceforge.net/project/fgrun/fgrun/1.5.2/fgrun-1.5.2.tar.gz?r=&ts=1296902151&use_mirror=puzzle)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://puzzle.dl.sourceforge.net/project/fgrun/fgrun/1.5.2/fgrun-1.5.2.tar.gz](http://puzzle.dl.sourceforge.net/project/fgrun/fgrun/1.5.2/fgrun-1.5.2.tar.gz) [following]
--2011-02-05 12:35:51--  [http://puzzle.dl.sourceforge.net/project/fgrun/fgrun/1.5.2/fgrun-1.5.2.tar.gz](http://puzzle.dl.sourceforge.net/project/fgrun/fgrun/1.5.2/fgrun-1.5.2.tar.gz)
Resolving puzzle.dl.sourceforge.net... 195.141.111.5
Connecting to puzzle.dl.sourceforge.net|195.141.111.5|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 386102 (377K) [application/x-gzip]
Saving to: `download.1'

100%[====================================================================>] 386,102      239K/s   in 1.6s    

2011-02-05 12:35:54 (239 KB/s) - `download.1' saved [386102/386102]

tar: This does not look like a tar archive
tar: Skipping to next header
tar: Exiting with failure status due to previous errors
--2011-02-05 12:35:54--  [ftp://mirrors.ibiblio.org/pub/mirrors/simgear/ftp/Source/SimGear-2.0.0.tar.gz](ftp://mirrors.ibiblio.org/pub/mirrors/simgear/ftp/Source/SimGear-2.0.0.tar.gz)
           => `SimGear-2.0.0.tar.gz'
Resolving mirrors.ibiblio.org... 152.19.134.44
Connecting to mirrors.ibiblio.org|152.19.134.44|:21... failed: Connection refused.
tar: SimGear-2.0.0.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
./downloadinstallfgrun.sh: line 22: cd: SimGear-2.0.0: No such file or directory
./downloadinstallfgrun.sh: line 23: ./configure: No such file or directory
./downloadinstallfgrun.sh: line 27: cd: fgrun-1.5.2: No such file or directory
./downloadinstallfgrun.sh: line 28: ./configure: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
rm: cannot remove `download': No such file or directory
rm: cannot remove `fgrun-1.5.2': No such file or directory
rm: cannot remove `SimGear-2.0.0': No such file or directory
Installation complete.  You should now be able to open fgrun by typing the following command into a terminal: fgrun
If there were any errors, send me a PM, or reply to the thread.  I will try to get a fix in ASAP.
Enjoy!

---

### Post by fabrixx on 2011-03-14
@JayKav
Its need simgear-dev to work

It works Thanks!! :D

---

### Post by ubudog on 2011-03-15
Glad it works for ya.

@JayCav, I need to look into this...

---

### Post by wheresmything on 2011-05-01
i keep getting "permission denied"
to wit, 

james@Andromeda-II:~$ cd /home/james
james@Andromeda-II:~$ ./downloadinstallfgrun.sh
bash: ./downloadinstallfgrun.sh: Permission denied
james@Andromeda-II:~$ sudo su
[sudo] password for james: 
root@Andromeda-II:/home/james# ./downloadinstallfgrun.sh
bash: ./downloadinstallfgrun.sh: Permission denied

help?

---

### Post by fabrixx on 2011-05-01
> **wheresmything said:**
> i keep getting "permission denied"
to wit, 

james@Andromeda-II:~$ cd /home/james
james@Andromeda-II:~$ ./downloadinstallfgrun.sh
bash: ./downloadinstallfgrun.sh: Permission denied
james@Andromeda-II:~$ sudo su
[sudo] password for james: 
root@Andromeda-II:/home/james# ./downloadinstallfgrun.sh
bash: ./downloadinstallfgrun.sh: Permission denied

help?

$ sudo ./downloadinstallfgrun.sh

---

### Post by ubudog on 2011-05-01
> **fabrixx said:**
> $ sudo ./downloadinstallfgrun.sh

Yep, try that.

---

### Post by 633Dh98 on 2011-05-25
Does not work in Ubuntu 10.10 64 bit.   Builds folders but no fgrun command that I can find.

---

### Post by 633Dh98 on 2011-05-25
```
mike@mike-GA-MA78LM-S2H:~/Downloads$ bash ./downloadinstallfgrun.sh
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libfltk1.1 is already the newest version.
libfltk1.1-dev is already the newest version.
zlib1g is already the newest version.
zlib1g-dev is already the newest version.
libalut-dev is already the newest version.
libalut0 is already the newest version.
libopenal-dev is already the newest version.
libopenal1 is already the newest version.
libplib-dev is already the newest version.
libplib1 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
--2011-05-25 15:50:36--  [http://sourceforge.net/projects/fgrun/files/fgrun/1.5.2/fgrun-1.5.2.tar.gz/download](http://sourceforge.net/projects/fgrun/files/fgrun/1.5.2/fgrun-1.5.2.tar.gz/download)
Resolving sourceforge.net... 216.34.181.60
Connecting to sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/project/fgrun/fgrun/1.5.2/fgrun-1.5.2.tar.gz?r=&ts=1306353040&use_mirror=surfnet](http://downloads.sourceforge.net/project/fgrun/fgrun/1.5.2/fgrun-1.5.2.tar.gz?r=&ts=1306353040&use_mirror=surfnet) [following]
--2011-05-25 15:50:41--  [http://downloads.sourceforge.net/project/fgrun/fgrun/1.5.2/fgrun-1.5.2.tar.gz?r=&ts=1306353040&use_mirror=surfnet](http://downloads.sourceforge.net/project/fgrun/fgrun/1.5.2/fgrun-1.5.2.tar.gz?r=&ts=1306353040&use_mirror=surfnet)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://surfnet.dl.sourceforge.net/project/fgrun/fgrun/1.5.2/fgrun-1.5.2.tar.gz](http://surfnet.dl.sourceforge.net/project/fgrun/fgrun/1.5.2/fgrun-1.5.2.tar.gz) [following]
--2011-05-25 15:50:41--  [http://surfnet.dl.sourceforge.net/project/fgrun/fgrun/1.5.2/fgrun-1.5.2.tar.gz](http://surfnet.dl.sourceforge.net/project/fgrun/fgrun/1.5.2/fgrun-1.5.2.tar.gz)
Resolving surfnet.dl.sourceforge.net... 130.59.138.21, 2001:620:0:1b::21
Connecting to surfnet.dl.sourceforge.net|130.59.138.21|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 386102 (377K) [application/x-gzip]
Saving to: `download'

100%[==========================================================================================>] 386,102      146K/s   in 2.6s    

2011-05-25 15:50:44 (146 KB/s) - `download' saved [386102/386102]

fgrun-1.5.2/
fgrun-1.5.2/m4/
fgrun-1.5.2/m4/lib-link.m4
fgrun-1.5.2/m4/po.m4
fgrun-1.5.2/m4/lib-ld.m4
fgrun-1.5.2/m4/iconv.m4
fgrun-1.5.2/m4/gettext.m4
fgrun-1.5.2/m4/nls.m4
fgrun-1.5.2/m4/progtest.m4
fgrun-1.5.2/m4/ChangeLog
fgrun-1.5.2/m4/lib-prefix.m4
fgrun-1.5.2/po/
fgrun-1.5.2/po/Makevars
fgrun-1.5.2/po/de.po
fgrun-1.5.2/po/es.po
fgrun-1.5.2/po/fr.po
fgrun-1.5.2/po/it.po
fgrun-1.5.2/po/LINGUAS
fgrun-1.5.2/po/nl.po
fgrun-1.5.2/po/pl.po
fgrun-1.5.2/po/pt.po
fgrun-1.5.2/po/en@boldquot.header
fgrun-1.5.2/po/en@quot.header
fgrun-1.5.2/po/Rules-quot
fgrun-1.5.2/po/remove-potcdate.sin
fgrun-1.5.2/po/boldquot.sed
fgrun-1.5.2/po/POTFILES.in
fgrun-1.5.2/po/de.gmo
fgrun-1.5.2/po/es.gmo
fgrun-1.5.2/po/fr.gmo
fgrun-1.5.2/po/it.gmo
fgrun-1.5.2/po/nl.gmo
fgrun-1.5.2/po/insert-header.sin
fgrun-1.5.2/po/pl.gmo
fgrun-1.5.2/po/pt.gmo
fgrun-1.5.2/po/stamp-po
fgrun-1.5.2/po/quot.sed
fgrun-1.5.2/po/ChangeLog
fgrun-1.5.2/po/Makefile.in.in
fgrun-1.5.2/po/fgrun.pot
fgrun-1.5.2/src/
fgrun-1.5.2/src/Fl_Table.cxx
fgrun-1.5.2/src/Fl_Table_Row.cxx
fgrun-1.5.2/src/os_win32.h
fgrun-1.5.2/src/fgrun_pty.cxx
fgrun-1.5.2/src/os_posix.h
fgrun-1.5.2/src/Fl_OSG.h
fgrun-1.5.2/src/AirportBrowser.cxx
fgrun-1.5.2/src/main.cxx
fgrun-1.5.2/src/advanced.cxx
fgrun-1.5.2/src/i18n.h
fgrun-1.5.2/src/AirportBrowser.h
fgrun-1.5.2/src/AirportTable.cxx
fgrun-1.5.2/src/Makefile.am
fgrun-1.5.2/src/Makefile.in
fgrun-1.5.2/src/io.cxx
fgrun-1.5.2/src/Fl_Table.H
fgrun-1.5.2/src/apt_dat.h
fgrun-1.5.2/src/Fl_Heading_Dial.H
fgrun-1.5.2/src/config.h.in
fgrun-1.5.2/src/Fl_OSG.cxx
fgrun-1.5.2/src/parkingloader.h
fgrun-1.5.2/src/settings.cxx
fgrun-1.5.2/src/Fl_Heading_Dial.cxx
fgrun-1.5.2/src/Fl_Table_Row.H
fgrun-1.5.2/src/util.h
fgrun-1.5.2/src/run_win32.cxx
fgrun-1.5.2/src/wizard.cxx
fgrun-1.5.2/src/AirportTable.h
fgrun-1.5.2/src/advanced.fl
fgrun-1.5.2/src/logwin.h
fgrun-1.5.2/src/wizard.fl
fgrun-1.5.2/src/wizard.h
fgrun-1.5.2/src/parkingloader.cxx
fgrun-1.5.2/src/fgfsrc.cxx
fgrun-1.5.2/src/run_posix.cxx
fgrun-1.5.2/src/advanced.h
fgrun-1.5.2/src/wizard_funcs.cxx
fgrun-1.5.2/src/fgrun_pty.h
fgrun-1.5.2/src/folder_open.xpm
fgrun-1.5.2/src/logwin.cxx
fgrun-1.5.2/src/util.cxx
fgrun-1.5.2/src/advanced_funcs.cxx
fgrun-1.5.2/NEWS
fgrun-1.5.2/msvc/
fgrun-1.5.2/msvc/6.0/
fgrun-1.5.2/msvc/6.0/fgrun.dsp
fgrun-1.5.2/msvc/6.0/fgrun.dsw
fgrun-1.5.2/msvc/7.1/
fgrun-1.5.2/msvc/7.1/fgrun.vcproj
fgrun-1.5.2/msvc/7.1/fgrun.sln
fgrun-1.5.2/depcomp
fgrun-1.5.2/aclocal.m4
fgrun-1.5.2/README
fgrun-1.5.2/configure
fgrun-1.5.2/fgrun.prefs
fgrun-1.5.2/configure.ac
fgrun-1.5.2/config.guess
fgrun-1.5.2/config.rpath
fgrun-1.5.2/install-sh
fgrun-1.5.2/autogen.sh
fgrun-1.5.2/config.sub
fgrun-1.5.2/missing
fgrun-1.5.2/Makefile.am
fgrun-1.5.2/Makefile.in
fgrun-1.5.2/acinclude.m4
fgrun-1.5.2/AUTHORS
fgrun-1.5.2/INSTALL
fgrun-1.5.2/ABOUT-NLS
fgrun-1.5.2/ChangeLog
fgrun-1.5.2/plib.m4
fgrun-1.5.2/COPYING
--2011-05-25 15:50:45--  [ftp://mirrors.ibiblio.org/pub/mirrors/simgear/ftp/Source/SimGear-2.0.0.tar.gz](ftp://mirrors.ibiblio.org/pub/mirrors/simgear/ftp/Source/SimGear-2.0.0.tar.gz)
           => `SimGear-2.0.0.tar.gz.1'
Resolving mirrors.ibiblio.org... 152.19.134.44
Connecting to mirrors.ibiblio.org|152.19.134.44|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD (1) /pub/mirrors/simgear/ftp/Source ... done.
==> SIZE SimGear-2.0.0.tar.gz ... 1058343
==> PASV ... done.    ==> RETR SimGear-2.0.0.tar.gz ... done.
Length: 1058343 (1.0M) (unauthoritative)

100%[==========================================================================================>] 1,058,343    228K/s   in 5.1s    

2011-05-25 15:50:50 (204 KB/s) - `SimGear-2.0.0.tar.gz.1' saved [1058343]

SimGear-2.0.0/
SimGear-2.0.0/README
SimGear-2.0.0/autogen.sh
SimGear-2.0.0/ChangeLog
SimGear-2.0.0/NEWS
SimGear-2.0.0/AUTHORS
SimGear-2.0.0/TODO
SimGear-2.0.0/DoxygenMain.cxx
SimGear-2.0.0/missing
SimGear-2.0.0/README.OpenAL
SimGear-2.0.0/configure
SimGear-2.0.0/README.plib
SimGear-2.0.0/simgear/
SimGear-2.0.0/simgear/version.h.in
SimGear-2.0.0/simgear/simgear_config.h-msvc71
SimGear-2.0.0/simgear/screen/
SimGear-2.0.0/simgear/screen/jpgfactory.cxx
SimGear-2.0.0/simgear/screen/win32-printer.h
SimGear-2.0.0/simgear/screen/extensions.cxx
SimGear-2.0.0/simgear/screen/GLBitmaps.cxx
SimGear-2.0.0/simgear/screen/RenderTexture.h
SimGear-2.0.0/simgear/screen/screen-dump.hxx
SimGear-2.0.0/simgear/screen/GLBitmaps.h
SimGear-2.0.0/simgear/screen/shader.h
SimGear-2.0.0/simgear/screen/jpgfactory.hxx
SimGear-2.0.0/simgear/screen/RenderTexture.cpp
SimGear-2.0.0/simgear/screen/tr.cxx
SimGear-2.0.0/simgear/screen/colors.hxx
SimGear-2.0.0/simgear/screen/extensions.hxx
SimGear-2.0.0/simgear/screen/TestRenderTexture.cpp
SimGear-2.0.0/simgear/screen/Makefile.in
SimGear-2.0.0/simgear/screen/shader.cpp
SimGear-2.0.0/simgear/screen/Makefile.am
SimGear-2.0.0/simgear/screen/screen-dump.cxx
SimGear-2.0.0/simgear/screen/tr.h
SimGear-2.0.0/simgear/misc/
SimGear-2.0.0/simgear/misc/texcoord.hxx
SimGear-2.0.0/simgear/misc/texcoord.cxx
SimGear-2.0.0/simgear/misc/interpolator.cxx
SimGear-2.0.0/simgear/misc/zfstream.cxx
SimGear-2.0.0/simgear/misc/PathOptions.hxx
SimGear-2.0.0/simgear/misc/sgstream.hxx
SimGear-2.0.0/simgear/misc/tabbed_values.cxx
SimGear-2.0.0/simgear/misc/strutils.hxx
SimGear-2.0.0/simgear/misc/stopwatch.hxx
SimGear-2.0.0/simgear/misc/interpolator.hxx
SimGear-2.0.0/simgear/misc/sg_path.cxx
SimGear-2.0.0/simgear/misc/stdint.hxx
SimGear-2.0.0/simgear/misc/tabbed_values.hxx
SimGear-2.0.0/simgear/misc/Makefile.in
SimGear-2.0.0/simgear/misc/sg_path.hxx
SimGear-2.0.0/simgear/misc/sgstream.cxx
SimGear-2.0.0/simgear/misc/strutils.cxx
SimGear-2.0.0/simgear/misc/Makefile.am
SimGear-2.0.0/simgear/misc/PathOptions.cxx
SimGear-2.0.0/simgear/misc/zfstream.hxx
SimGear-2.0.0/simgear/nasal/
SimGear-2.0.0/simgear/nasal/iolib.c
SimGear-2.0.0/simgear/nasal/bitslib.c
SimGear-2.0.0/simgear/nasal/nasal.h
SimGear-2.0.0/simgear/nasal/parse.c
SimGear-2.0.0/simgear/nasal/thread-win32.c
SimGear-2.0.0/simgear/nasal/gc.c
SimGear-2.0.0/simgear/nasal/code.c
SimGear-2.0.0/simgear/nasal/parse.h
SimGear-2.0.0/simgear/nasal/data.h
SimGear-2.0.0/simgear/nasal/mathlib.c
SimGear-2.0.0/simgear/nasal/iolib.h
SimGear-2.0.0/simgear/nasal/codegen.c
SimGear-2.0.0/simgear/nasal/string.c
SimGear-2.0.0/simgear/nasal/misc.c
SimGear-2.0.0/simgear/nasal/lib.c
SimGear-2.0.0/simgear/nasal/naref.h
SimGear-2.0.0/simgear/nasal/hash.c
SimGear-2.0.0/simgear/nasal/Makefile.in
SimGear-2.0.0/simgear/nasal/vector.c
SimGear-2.0.0/simgear/nasal/threadlib.c
SimGear-2.0.0/simgear/nasal/lex.c
SimGear-2.0.0/simgear/nasal/Makefile.am
SimGear-2.0.0/simgear/nasal/utf8lib.c
SimGear-2.0.0/simgear/nasal/thread-posix.c
SimGear-2.0.0/simgear/nasal/code.h
SimGear-2.0.0/simgear/debug/
SimGear-2.0.0/simgear/debug/logtest.cxx
SimGear-2.0.0/simgear/debug/debug_types.h
SimGear-2.0.0/simgear/debug/logstream.cxx
SimGear-2.0.0/simgear/debug/logstream.hxx
SimGear-2.0.0/simgear/debug/Makefile.in
SimGear-2.0.0/simgear/debug/Makefile.am
SimGear-2.0.0/simgear/compiler.h
SimGear-2.0.0/simgear/io/
SimGear-2.0.0/simgear/io/sg_socket_udp.cxx
SimGear-2.0.0/simgear/io/decode_binobj.cxx
SimGear-2.0.0/simgear/io/sg_binobj.cxx
SimGear-2.0.0/simgear/io/socktest.cxx
SimGear-2.0.0/simgear/io/sg_socket.hxx
SimGear-2.0.0/simgear/io/tcp_client.cxx
SimGear-2.0.0/simgear/io/sg_socket.cxx
SimGear-2.0.0/simgear/io/sg_file.hxx
SimGear-2.0.0/simgear/io/lowtest.cxx
SimGear-2.0.0/simgear/io/sg_socket_udp.hxx
SimGear-2.0.0/simgear/io/lowlevel.cxx
SimGear-2.0.0/simgear/io/sg_binobj.hxx
SimGear-2.0.0/simgear/io/lowlevel.hxx
SimGear-2.0.0/simgear/io/iochannel.hxx
SimGear-2.0.0/simgear/io/iochannel.cxx
SimGear-2.0.0/simgear/io/Makefile.in
SimGear-2.0.0/simgear/io/sg_serial.hxx
SimGear-2.0.0/simgear/io/sg_file.cxx
SimGear-2.0.0/simgear/io/Makefile.am
SimGear-2.0.0/simgear/io/tcp_server.cxx
SimGear-2.0.0/simgear/io/sg_serial.cxx
SimGear-2.0.0/simgear/compatibility/
SimGear-2.0.0/simgear/compatibility/MIPSpro721/
SimGear-2.0.0/simgear/compatibility/MIPSpro721/iostream
SimGear-2.0.0/simgear/compatibility/MIPSpro721/irix_string
SimGear-2.0.0/simgear/compatibility/MIPSpro721/sstream
SimGear-2.0.0/simgear/compatibility/MIPSpro721/istream
SimGear-2.0.0/simgear/compatibility/MIPSpro721/streambuf
SimGear-2.0.0/simgear/compatibility/MIPSpro721/iterator
SimGear-2.0.0/simgear/compatibility/MIPSpro721/new
SimGear-2.0.0/simgear/compatibility/MIPSpro721/iomanip
SimGear-2.0.0/simgear/compatibility/MIPSpro721/fstream
SimGear-2.0.0/simgear/compatibility/MIPSpro721/Makefile.in
SimGear-2.0.0/simgear/compatibility/MIPSpro721/Makefile.am
SimGear-2.0.0/simgear/compatibility/MIPSpro721/strstream
SimGear-2.0.0/simgear/compatibility/MIPSpro740/
SimGear-2.0.0/simgear/compatibility/MIPSpro740/cctype
SimGear-2.0.0/simgear/compatibility/MIPSpro740/README
SimGear-2.0.0/simgear/compatibility/MIPSpro740/clocale
SimGear-2.0.0/simgear/compatibility/MIPSpro740/cstring
SimGear-2.0.0/simgear/compatibility/MIPSpro740/ctime
SimGear-2.0.0/simgear/compatibility/MIPSpro740/cstddef
SimGear-2.0.0/simgear/compatibility/MIPSpro740/csetjmp
SimGear-2.0.0/simgear/compatibility/MIPSpro740/cstdio
SimGear-2.0.0/simgear/compatibility/MIPSpro740/cstdlib
SimGear-2.0.0/simgear/compatibility/MIPSpro740/cwchar
SimGear-2.0.0/simgear/compatibility/MIPSpro740/cstdarg
SimGear-2.0.0/simgear/compatibility/MIPSpro740/cassert
SimGear-2.0.0/simgear/compatibility/MIPSpro740/cfloat
SimGear-2.0.0/simgear/compatibility/MIPSpro740/cmath
SimGear-2.0.0/simgear/compatibility/MIPSpro740/cwctype
SimGear-2.0.0/simgear/compatibility/MIPSpro740/Makefile.in
SimGear-2.0.0/simgear/compatibility/MIPSpro740/cerrno
SimGear-2.0.0/simgear/compatibility/MIPSpro740/csignal
SimGear-2.0.0/simgear/compatibility/MIPSpro740/climits
SimGear-2.0.0/simgear/compatibility/MIPSpro740/Makefile.am
SimGear-2.0.0/simgear/compatibility/Makefile.in
SimGear-2.0.0/simgear/compatibility/Makefile.am
SimGear-2.0.0/simgear/props/
SimGear-2.0.0/simgear/props/props_test.cxx
SimGear-2.0.0/simgear/props/condition.hxx
SimGear-2.0.0/simgear/props/AtomicChangeListener.hxx
SimGear-2.0.0/simgear/props/ExtendedPropertyAdapter.hxx
SimGear-2.0.0/simgear/props/props.hxx
SimGear-2.0.0/simgear/props/AtomicChangeListener.cxx
SimGear-2.0.0/simgear/props/props_io.cxx
SimGear-2.0.0/simgear/props/props.cxx
SimGear-2.0.0/simgear/props/Makefile.in
SimGear-2.0.0/simgear/props/props_io.hxx
SimGear-2.0.0/simgear/props/condition.cxx
SimGear-2.0.0/simgear/props/Makefile.am
SimGear-2.0.0/simgear/xml/
SimGear-2.0.0/simgear/xml/utf8tab.h
SimGear-2.0.0/simgear/xml/iasciitab.h
SimGear-2.0.0/simgear/xml/easyxml.cxx
SimGear-2.0.0/simgear/xml/xmldef.h
SimGear-2.0.0/simgear/xml/xmlrole.h
SimGear-2.0.0/simgear/xml/asciitab.h
SimGear-2.0.0/simgear/xml/xmlrole.c
SimGear-2.0.0/simgear/xml/xmltok.c
SimGear-2.0.0/simgear/xml/xmltok_impl.h
SimGear-2.0.0/simgear/xml/xmlparse.h
SimGear-2.0.0/simgear/xml/hashtable.h
SimGear-2.0.0/simgear/xml/easyxml.hxx
SimGear-2.0.0/simgear/xml/xmltok_impl.c
SimGear-2.0.0/simgear/xml/latin1tab.h
SimGear-2.0.0/simgear/xml/nametab.h
SimGear-2.0.0/simgear/xml/xmltok.h
SimGear-2.0.0/simgear/xml/xmlparse.c
SimGear-2.0.0/simgear/xml/Makefile.in
SimGear-2.0.0/simgear/xml/Makefile.am
SimGear-2.0.0/simgear/xml/hashtable.c
SimGear-2.0.0/simgear/xml/xmltok_ns.c
SimGear-2.0.0/simgear/timing/
SimGear-2.0.0/simgear/timing/geocoord.cxx
SimGear-2.0.0/simgear/timing/timezone.h
SimGear-2.0.0/simgear/timing/sg_time.cxx
SimGear-2.0.0/simgear/timing/lowleveltime.h
SimGear-2.0.0/simgear/timing/timestamp.cxx
SimGear-2.0.0/simgear/timing/timestamp.hxx
SimGear-2.0.0/simgear/timing/lowleveltime.cxx
SimGear-2.0.0/simgear/timing/Makefile.in
SimGear-2.0.0/simgear/timing/sg_time.hxx
SimGear-2.0.0/simgear/timing/timezone.cxx
SimGear-2.0.0/simgear/timing/Makefile.am
SimGear-2.0.0/simgear/timing/geocoord.h
SimGear-2.0.0/simgear/simgear_config.h.in
SimGear-2.0.0/simgear/bucket/
SimGear-2.0.0/simgear/bucket/newbucket.hxx
SimGear-2.0.0/simgear/bucket/newbucket.cxx
SimGear-2.0.0/simgear/bucket/Makefile.in
SimGear-2.0.0/simgear/bucket/Makefile.am
SimGear-2.0.0/simgear/route/
SimGear-2.0.0/simgear/route/routetest.cxx
SimGear-2.0.0/simgear/route/waypoint.cxx
SimGear-2.0.0/simgear/route/waypoint.hxx
SimGear-2.0.0/simgear/route/route.hxx
SimGear-2.0.0/simgear/route/Makefile.in
SimGear-2.0.0/simgear/route/waytest.cxx
SimGear-2.0.0/simgear/route/route.cxx
SimGear-2.0.0/simgear/route/Makefile.am
SimGear-2.0.0/simgear/threads/
SimGear-2.0.0/simgear/threads/SGQueue.hxx
SimGear-2.0.0/simgear/threads/SGThread.hxx
SimGear-2.0.0/simgear/threads/Makefile.in
SimGear-2.0.0/simgear/threads/SGGuard.hxx
SimGear-2.0.0/simgear/threads/SGThread.cxx
SimGear-2.0.0/simgear/threads/Makefile.am
SimGear-2.0.0/simgear/simgear_config.h.vc5
SimGear-2.0.0/simgear/ephemeris/
SimGear-2.0.0/simgear/ephemeris/mars.cxx
SimGear-2.0.0/simgear/ephemeris/venus.cxx
SimGear-2.0.0/simgear/ephemeris/moonpos.cxx
SimGear-2.0.0/simgear/ephemeris/venus.hxx
SimGear-2.0.0/simgear/ephemeris/jupiter.hxx
SimGear-2.0.0/simgear/ephemeris/pluto.hxx
SimGear-2.0.0/simgear/ephemeris/jupiter.cxx
SimGear-2.0.0/simgear/ephemeris/ephemeris.hxx
SimGear-2.0.0/simgear/ephemeris/saturn.hxx
SimGear-2.0.0/simgear/ephemeris/saturn.cxx
SimGear-2.0.0/simgear/ephemeris/uranus.cxx
SimGear-2.0.0/simgear/ephemeris/celestialBody.hxx
SimGear-2.0.0/simgear/ephemeris/stardata.cxx
SimGear-2.0.0/simgear/ephemeris/moonpos.hxx
SimGear-2.0.0/simgear/ephemeris/stardata.hxx
SimGear-2.0.0/simgear/ephemeris/mercury.hxx
SimGear-2.0.0/simgear/ephemeris/mars.hxx
SimGear-2.0.0/simgear/ephemeris/neptune.hxx
SimGear-2.0.0/simgear/ephemeris/neptune.cxx
SimGear-2.0.0/simgear/ephemeris/Makefile.in
SimGear-2.0.0/simgear/ephemeris/ephemeris.cxx
SimGear-2.0.0/simgear/ephemeris/mercury.cxx
SimGear-2.0.0/simgear/ephemeris/star.cxx
SimGear-2.0.0/simgear/ephemeris/Makefile.am
SimGear-2.0.0/simgear/ephemeris/star.hxx
SimGear-2.0.0/simgear/ephemeris/uranus.hxx
SimGear-2.0.0/simgear/ephemeris/celestialBody.cxx
SimGear-2.0.0/simgear/structure/
SimGear-2.0.0/simgear/structure/OSGUtils.hxx
SimGear-2.0.0/simgear/structure/SGBinding.cxx
SimGear-2.0.0/simgear/structure/commands.cxx
SimGear-2.0.0/simgear/structure/event_mgr.hxx
SimGear-2.0.0/simgear/structure/SGSmplhist.cxx
SimGear-2.0.0/simgear/structure/SGSharedPtr.hxx
SimGear-2.0.0/simgear/structure/StringTable.hxx
SimGear-2.0.0/simgear/structure/SGSmplhist.hxx
SimGear-2.0.0/simgear/structure/SGExpression.cxx
SimGear-2.0.0/simgear/structure/event_mgr.cxx
SimGear-2.0.0/simgear/structure/intern.hxx
SimGear-2.0.0/simgear/structure/SGSmplstat.hxx
SimGear-2.0.0/simgear/structure/Singleton.hxx
SimGear-2.0.0/simgear/structure/SGWeakReferenced.hxx
SimGear-2.0.0/simgear/structure/commands.hxx
SimGear-2.0.0/simgear/structure/StringTable.cxx
SimGear-2.0.0/simgear/structure/SGExpression.hxx
SimGear-2.0.0/simgear/structure/exception.cxx
SimGear-2.0.0/simgear/structure/SGAtomic.hxx
SimGear-2.0.0/simgear/structure/SGAtomic.cxx
SimGear-2.0.0/simgear/structure/SGWeakPtr.hxx
SimGear-2.0.0/simgear/structure/SGSmplstat.cxx
SimGear-2.0.0/simgear/structure/callback.hxx
SimGear-2.0.0/simgear/structure/Makefile.in
SimGear-2.0.0/simgear/structure/subsystem_mgr.hxx
SimGear-2.0.0/simgear/structure/SGReferenced.hxx
SimGear-2.0.0/simgear/structure/Makefile.am
SimGear-2.0.0/simgear/structure/OSGVersion.hxx
SimGear-2.0.0/simgear/structure/subsystem_mgr.cxx
SimGear-2.0.0/simgear/structure/exception.hxx
SimGear-2.0.0/simgear/structure/SGBinding.hxx
SimGear-2.0.0/simgear/version.h
SimGear-2.0.0/simgear/constants.h
SimGear-2.0.0/simgear/scene/
SimGear-2.0.0/simgear/scene/tgdb/
SimGear-2.0.0/simgear/scene/tgdb/ReaderWriterSTG.hxx
SimGear-2.0.0/simgear/scene/tgdb/SGVertexArrayBin.hxx
SimGear-2.0.0/simgear/scene/tgdb/apt_signs.cxx
SimGear-2.0.0/simgear/scene/tgdb/SGTexturedTriangleBin.hxx
SimGear-2.0.0/simgear/scene/tgdb/TileCache.cxx
SimGear-2.0.0/simgear/scene/tgdb/SGVasiDrawable.hxx
SimGear-2.0.0/simgear/scene/tgdb/GroundLightManager.hxx
SimGear-2.0.0/simgear/scene/tgdb/userdata.hxx
SimGear-2.0.0/simgear/scene/tgdb/TreeBin.hxx
SimGear-2.0.0/simgear/scene/tgdb/pt_lights.hxx
SimGear-2.0.0/simgear/scene/tgdb/SGOceanTile.hxx
SimGear-2.0.0/simgear/scene/tgdb/apt_signs.hxx
SimGear-2.0.0/simgear/scene/tgdb/TileEntry.cxx
SimGear-2.0.0/simgear/scene/tgdb/TreeBin.cxx
SimGear-2.0.0/simgear/scene/tgdb/SGReaderWriterBTGOptions.hxx
SimGear-2.0.0/simgear/scene/tgdb/SGTriangleBin.hxx
SimGear-2.0.0/simgear/scene/tgdb/ShaderGeometry.cxx
SimGear-2.0.0/simgear/scene/tgdb/pt_lights.cxx
SimGear-2.0.0/simgear/scene/tgdb/SGVasiDrawable.cxx
SimGear-2.0.0/simgear/scene/tgdb/obj.cxx
SimGear-2.0.0/simgear/scene/tgdb/ReaderWriterSTG.cxx
SimGear-2.0.0/simgear/scene/tgdb/TileEntry.hxx
SimGear-2.0.0/simgear/scene/tgdb/SGLightBin.hxx
SimGear-2.0.0/simgear/scene/tgdb/ShaderGeometry.hxx
SimGear-2.0.0/simgear/scene/tgdb/SGReaderWriterBTG.hxx
SimGear-2.0.0/simgear/scene/tgdb/GroundLightManager.cxx
SimGear-2.0.0/simgear/scene/tgdb/obj.hxx
SimGear-2.0.0/simgear/scene/tgdb/TileCache.hxx
SimGear-2.0.0/simgear/scene/tgdb/SGModelBin.hxx
SimGear-2.0.0/simgear/scene/tgdb/userdata.cxx
SimGear-2.0.0/simgear/scene/tgdb/Makefile.in
SimGear-2.0.0/simgear/scene/tgdb/SGReaderWriterBTG.cxx
SimGear-2.0.0/simgear/scene/tgdb/SGDirectionalLightBin.hxx
SimGear-2.0.0/simgear/scene/tgdb/Makefile.am
SimGear-2.0.0/simgear/scene/tgdb/SGOceanTile.cxx
SimGear-2.0.0/simgear/scene/model/
SimGear-2.0.0/simgear/scene/model/SGMaterialAnimation.cxx
SimGear-2.0.0/simgear/scene/model/shadanim.cxx
SimGear-2.0.0/simgear/scene/model/model.cxx
SimGear-2.0.0/simgear/scene/model/ModelRegistry.cxx
SimGear-2.0.0/simgear/scene/model/SGInteractionAnimation.cxx
SimGear-2.0.0/simgear/scene/model/BoundingVolumeBuildVisitor.hxx
SimGear-2.0.0/simgear/scene/model/persparam.cxx
SimGear-2.0.0/simgear/scene/model/SGInteractionAnimation.hxx
SimGear-2.0.0/simgear/scene/model/modellib.cxx
SimGear-2.0.0/simgear/scene/model/SGOffsetTransform.cxx
SimGear-2.0.0/simgear/scene/model/SGPagedLOD.hxx
SimGear-2.0.0/simgear/scene/model/SGRotateTransform.hxx
SimGear-2.0.0/simgear/scene/model/particles.cxx
SimGear-2.0.0/simgear/scene/model/SGMaterialAnimation.hxx
SimGear-2.0.0/simgear/scene/model/SGReaderWriterXMLOptions.hxx
SimGear-2.0.0/simgear/scene/model/CheckSceneryVisitor.hxx
SimGear-2.0.0/simgear/scene/model/particles.hxx
SimGear-2.0.0/simgear/scene/model/SGText.cxx
SimGear-2.0.0/simgear/scene/model/SGText.hxx
SimGear-2.0.0/simgear/scene/model/SGOffsetTransform.hxx
SimGear-2.0.0/simgear/scene/model/SGReaderWriterXML.cxx
SimGear-2.0.0/simgear/scene/model/SGClipGroup.hxx
SimGear-2.0.0/simgear/scene/model/animation.cxx
SimGear-2.0.0/simgear/scene/model/SGReaderWriterXML.hxx
SimGear-2.0.0/simgear/scene/model/placement.cxx
SimGear-2.0.0/simgear/scene/model/SGTranslateTransform.hxx
SimGear-2.0.0/simgear/scene/model/persparam.hxx
SimGear-2.0.0/simgear/scene/model/CheckSceneryVisitor.cxx
SimGear-2.0.0/simgear/scene/model/SGScaleTransform.cxx
SimGear-2.0.0/simgear/scene/model/SGRotateTransform.cxx
SimGear-2.0.0/simgear/scene/model/SGTranslateTransform.cxx
SimGear-2.0.0/simgear/scene/model/Makefile.in
SimGear-2.0.0/simgear/scene/model/SGClipGroup.cxx
SimGear-2.0.0/simgear/scene/model/animation.hxx
SimGear-2.0.0/simgear/scene/model/SGScaleTransform.hxx
SimGear-2.0.0/simgear/scene/model/placement.hxx
SimGear-2.0.0/simgear/scene/model/SGPagedLOD.cxx
SimGear-2.0.0/simgear/scene/model/modellib.hxx
SimGear-2.0.0/simgear/scene/model/Makefile.am
SimGear-2.0.0/simgear/scene/model/ModelRegistry.hxx
SimGear-2.0.0/simgear/scene/model/model.hxx
SimGear-2.0.0/simgear/scene/util/
SimGear-2.0.0/simgear/scene/util/UpdateOnceCallback.hxx
SimGear-2.0.0/simgear/scene/util/QuadTreeBuilder.cxx
SimGear-2.0.0/simgear/scene/util/SGSceneUserData.cxx
SimGear-2.0.0/simgear/scene/util/SGTextureStateAttributeVisitor.hxx
SimGear-2.0.0/simgear/scene/util/SplicingVisitor.cxx
SimGear-2.0.0/simgear/scene/util/PrimitiveUtils.cxx
SimGear-2.0.0/simgear/scene/util/SGEnlargeBoundingBox.hxx
SimGear-2.0.0/simgear/scene/util/QuadTreeBuilder.hxx
SimGear-2.0.0/simgear/scene/util/SGDebugDrawCallback.hxx
SimGear-2.0.0/simgear/scene/util/NodeAndDrawableVisitor.hxx
SimGear-2.0.0/simgear/scene/util/RenderConstants.hxx
SimGear-2.0.0/simgear/scene/util/SGUpdateVisitor.hxx
SimGear-2.0.0/simgear/scene/util/CopyOp.hxx
SimGear-2.0.0/simgear/scene/util/PrimitiveUtils.hxx
SimGear-2.0.0/simgear/scene/util/StateAttributeFactory.hxx
SimGear-2.0.0/simgear/scene/util/StateAttributeFactory.cxx
SimGear-2.0.0/simgear/scene/util/SGPickCallback.hxx
SimGear-2.0.0/simgear/scene/util/SGStateAttributeVisitor.cxx
SimGear-2.0.0/simgear/scene/util/VectorArrayAdapter.hxx
SimGear-2.0.0/simgear/scene/util/SGSceneFeatures.hxx
SimGear-2.0.0/simgear/scene/util/SGStateAttributeVisitor.hxx
SimGear-2.0.0/simgear/scene/util/SGSceneUserData.hxx
SimGear-2.0.0/simgear/scene/util/SGTextureStateAttributeVisitor.cxx
SimGear-2.0.0/simgear/scene/util/UpdateOnceCallback.cxx
SimGear-2.0.0/simgear/scene/util/SGSceneFeatures.cxx
SimGear-2.0.0/simgear/scene/util/SGEnlargeBoundingBox.cxx
SimGear-2.0.0/simgear/scene/util/SplicingVisitor.hxx
SimGear-2.0.0/simgear/scene/util/Makefile.in
SimGear-2.0.0/simgear/scene/util/NodeAndDrawableVisitor.cxx
SimGear-2.0.0/simgear/scene/util/SGNodeMasks.hxx
SimGear-2.0.0/simgear/scene/util/CopyOp.cxx
SimGear-2.0.0/simgear/scene/util/Makefile.am
SimGear-2.0.0/simgear/scene/material/
SimGear-2.0.0/simgear/scene/material/matmodel.hxx
SimGear-2.0.0/simgear/scene/material/matlib.hxx
SimGear-2.0.0/simgear/scene/material/Pass.hxx
SimGear-2.0.0/simgear/scene/material/GLPredicate.hxx
SimGear-2.0.0/simgear/scene/material/TextureBuilder.cxx
SimGear-2.0.0/simgear/scene/material/matmodel.cxx
SimGear-2.0.0/simgear/scene/material/Technique.hxx
SimGear-2.0.0/simgear/scene/material/EffectGeode.hxx
SimGear-2.0.0/simgear/scene/material/EffectGeode.cxx
SimGear-2.0.0/simgear/scene/material/TextureBuilder.hxx
SimGear-2.0.0/simgear/scene/material/EffectBuilder.cxx
SimGear-2.0.0/simgear/scene/material/mat.hxx
SimGear-2.0.0/simgear/scene/material/Noise.cxx
SimGear-2.0.0/simgear/scene/material/EffectCullVisitor.cxx
SimGear-2.0.0/simgear/scene/material/matlib.cxx
SimGear-2.0.0/simgear/scene/material/GLPredicate.cxx
SimGear-2.0.0/simgear/scene/material/mat.cxx
SimGear-2.0.0/simgear/scene/material/Technique.cxx
SimGear-2.0.0/simgear/scene/material/EffectCullVisitor.hxx
SimGear-2.0.0/simgear/scene/material/Pass.cxx
SimGear-2.0.0/simgear/scene/material/Effect.hxx
SimGear-2.0.0/simgear/scene/material/makeEffect.cxx
SimGear-2.0.0/simgear/scene/material/Makefile.in
SimGear-2.0.0/simgear/scene/material/EffectBuilder.hxx
SimGear-2.0.0/simgear/scene/material/Makefile.am
SimGear-2.0.0/simgear/scene/material/Effect.cxx
SimGear-2.0.0/simgear/scene/material/Noise.hxx
SimGear-2.0.0/simgear/scene/sky/
SimGear-2.0.0/simgear/scene/sky/dome.hxx
SimGear-2.0.0/simgear/scene/sky/cloud.cxx
SimGear-2.0.0/simgear/scene/sky/moon.hxx
SimGear-2.0.0/simgear/scene/sky/bbcache.hxx
SimGear-2.0.0/simgear/scene/sky/oursun.cxx
SimGear-2.0.0/simgear/scene/sky/oursun.hxx
SimGear-2.0.0/simgear/scene/sky/cloudfield.hxx
SimGear-2.0.0/simgear/scene/sky/newcloud.cxx
SimGear-2.0.0/simgear/scene/sky/dome.cxx
SimGear-2.0.0/simgear/scene/sky/stars.cxx
SimGear-2.0.0/simgear/scene/sky/bbcache.cxx
SimGear-2.0.0/simgear/scene/sky/newcloud.hxx
SimGear-2.0.0/simgear/scene/sky/sky.cxx
SimGear-2.0.0/simgear/scene/sky/Makefile.in
SimGear-2.0.0/simgear/scene/sky/sky.hxx
SimGear-2.0.0/simgear/scene/sky/CloudShaderGeometry.cxx
SimGear-2.0.0/simgear/scene/sky/cloudfield.cxx
SimGear-2.0.0/simgear/scene/sky/Makefile.am
SimGear-2.0.0/simgear/scene/sky/moon.cxx
SimGear-2.0.0/simgear/scene/sky/sphere.hxx
SimGear-2.0.0/simgear/scene/sky/cloud.hxx
SimGear-2.0.0/simgear/scene/sky/stars.hxx
SimGear-2.0.0/simgear/scene/sky/sphere.cxx
SimGear-2.0.0/simgear/scene/sky/CloudShaderGeometry.hxx
SimGear-2.0.0/simgear/scene/bvh/
SimGear-2.0.0/simgear/scene/bvh/BVHLineSegmentVisitor.cxx
SimGear-2.0.0/simgear/scene/bvh/BVHNode.hxx
SimGear-2.0.0/simgear/scene/bvh/BVHStaticData.hxx
SimGear-2.0.0/simgear/scene/bvh/BVHDebugCollectVisitor.hxx
SimGear-2.0.0/simgear/scene/bvh/BVHLineGeometry.cxx
SimGear-2.0.0/simgear/scene/bvh/BVHStaticLeaf.hxx
SimGear-2.0.0/simgear/scene/bvh/BVHTransform.cxx
SimGear-2.0.0/simgear/scene/bvh/BVHStaticGeometryBuilder.hxx
SimGear-2.0.0/simgear/scene/bvh/BVHStaticGeometry.hxx
SimGear-2.0.0/simgear/scene/bvh/BVHMotionTransform.cxx
SimGear-2.0.0/simgear/scene/bvh/BVHGroup.cxx
SimGear-2.0.0/simgear/scene/bvh/bvhtest.cxx
SimGear-2.0.0/simgear/scene/bvh/BVHBoundingBoxVisitor.hxx
SimGear-2.0.0/simgear/scene/bvh/BVHSubTreeCollector.hxx
SimGear-2.0.0/simgear/scene/bvh/BVHStaticLeaf.cxx
SimGear-2.0.0/simgear/scene/bvh/BVHMotionTransform.hxx
SimGear-2.0.0/simgear/scene/bvh/BVHStaticNode.hxx
SimGear-2.0.0/simgear/scene/bvh/BVHStaticBinary.hxx
SimGear-2.0.0/simgear/scene/bvh/BVHLineGeometry.hxx
SimGear-2.0.0/simgear/scene/bvh/BVHSubTreeCollector.cxx
SimGear-2.0.0/simgear/scene/bvh/BVHStaticNode.cxx
SimGear-2.0.0/simgear/scene/bvh/BVHVisitor.hxx
SimGear-2.0.0/simgear/scene/bvh/BVHStaticBinary.cxx
SimGear-2.0.0/simgear/scene/bvh/BVHTransform.hxx
SimGear-2.0.0/simgear/scene/bvh/BVHLineSegmentVisitor.hxx
SimGear-2.0.0/simgear/scene/bvh/BVHStaticTriangle.hxx
SimGear-2.0.0/simgear/scene/bvh/BVHNearestPointVisitor.hxx
SimGear-2.0.0/simgear/scene/bvh/Makefile.in
SimGear-2.0.0/simgear/scene/bvh/BVHStaticGeometry.cxx
SimGear-2.0.0/simgear/scene/bvh/BVHNode.cxx
SimGear-2.0.0/simgear/scene/bvh/BVHGroup.hxx
SimGear-2.0.0/simgear/scene/bvh/Makefile.am
SimGear-2.0.0/simgear/scene/bvh/BVHStaticTriangle.cxx
SimGear-2.0.0/simgear/scene/Makefile.in
SimGear-2.0.0/simgear/scene/Makefile.am
SimGear-2.0.0/simgear/serial/
SimGear-2.0.0/simgear/serial/serial.cxx
SimGear-2.0.0/simgear/serial/serial.hxx
SimGear-2.0.0/simgear/serial/testserial.cxx
SimGear-2.0.0/simgear/serial/Makefile.in
SimGear-2.0.0/simgear/serial/Makefile.am
SimGear-2.0.0/simgear/Makefile.in
SimGear-2.0.0/simgear/environment/
SimGear-2.0.0/simgear/environment/metar.hxx
SimGear-2.0.0/simgear/environment/precipitation.cxx
SimGear-2.0.0/simgear/environment/metar.cxx
SimGear-2.0.0/simgear/environment/visual_enviro.cxx
SimGear-2.0.0/simgear/environment/visual_enviro.hxx
SimGear-2.0.0/simgear/environment/Makefile.in
SimGear-2.0.0/simgear/environment/precipitation.hxx
SimGear-2.0.0/simgear/environment/Makefile.am
SimGear-2.0.0/simgear/magvar/
SimGear-2.0.0/simgear/magvar/magvar.cxx
SimGear-2.0.0/simgear/magvar/coremag.cxx
SimGear-2.0.0/simgear/magvar/testmagvar.cxx
SimGear-2.0.0/simgear/magvar/Makefile.in
SimGear-2.0.0/simgear/magvar/magvar.hxx
SimGear-2.0.0/simgear/magvar/coremag.hxx
SimGear-2.0.0/simgear/magvar/Makefile.am
SimGear-2.0.0/simgear/sg_inlines.h
SimGear-2.0.0/simgear/Makefile.am
SimGear-2.0.0/simgear/math/
SimGear-2.0.0/simgear/math/SGMisc.hxx
SimGear-2.0.0/simgear/math/SGRay.hxx
SimGear-2.0.0/simgear/math/sg_geodesy.hxx
SimGear-2.0.0/simgear/math/SGGeodesy.cxx
SimGear-2.0.0/simgear/math/point3d.hxx
SimGear-2.0.0/simgear/math/SGGeometryFwd.hxx
SimGear-2.0.0/simgear/math/SGMathFwd.hxx
SimGear-2.0.0/simgear/math/Math.hxx
SimGear-2.0.0/simgear/math/beziercurve.hxx
SimGear-2.0.0/simgear/math/SGGeodesy.hxx
SimGear-2.0.0/simgear/math/SGBox.hxx
SimGear-2.0.0/simgear/math/SGSphere.hxx
SimGear-2.0.0/simgear/math/SGMathTest.cxx
SimGear-2.0.0/simgear/math/SGCMath.hxx
SimGear-2.0.0/simgear/math/SGPlane.hxx
SimGear-2.0.0/simgear/math/SGIntersect.hxx
SimGear-2.0.0/simgear/math/sg_types.hxx
SimGear-2.0.0/simgear/math/SGTriangle.hxx
SimGear-2.0.0/simgear/math/sg_random.c
SimGear-2.0.0/simgear/math/sg_random.h
SimGear-2.0.0/simgear/math/vector.hxx
SimGear-2.0.0/simgear/math/SGLimits.hxx
SimGear-2.0.0/simgear/math/SGGeometryTest.cxx
SimGear-2.0.0/simgear/math/leastsqs.cxx
SimGear-2.0.0/simgear/math/SGGeod.cxx
SimGear-2.0.0/simgear/math/SGQuat.hxx
SimGear-2.0.0/simgear/math/vector.cxx
SimGear-2.0.0/simgear/math/SGVec2.hxx
SimGear-2.0.0/simgear/math/interpolater.cxx
SimGear-2.0.0/simgear/math/SGMatrix.hxx
SimGear-2.0.0/simgear/math/interpolater.hxx
SimGear-2.0.0/simgear/math/leastsqs.hxx
SimGear-2.0.0/simgear/math/SGVec4.hxx
SimGear-2.0.0/simgear/math/SGVec3.hxx
SimGear-2.0.0/simgear/math/Makefile.in
SimGear-2.0.0/simgear/math/SGGeoc.hxx
SimGear-2.0.0/simgear/math/SGMath.hxx
SimGear-2.0.0/simgear/math/SGGeometry.hxx
SimGear-2.0.0/simgear/math/SGLineSegment.hxx
SimGear-2.0.0/simgear/math/Makefile.am
SimGear-2.0.0/simgear/math/SGGeod.hxx
SimGear-2.0.0/simgear/math/polar3d.hxx
SimGear-2.0.0/simgear/sound/
SimGear-2.0.0/simgear/sound/README
SimGear-2.0.0/simgear/sound/soundmgr_openal.cxx
SimGear-2.0.0/simgear/sound/xmlsound.cxx
SimGear-2.0.0/simgear/sound/sample_group.hxx
SimGear-2.0.0/simgear/sound/openal_test1.cxx
SimGear-2.0.0/simgear/sound/soundmgr_openal.hxx
SimGear-2.0.0/simgear/sound/openal_test2.cxx
SimGear-2.0.0/simgear/sound/sample_openal.hxx
SimGear-2.0.0/simgear/sound/sample_group.cxx
SimGear-2.0.0/simgear/sound/xmlsound.hxx
SimGear-2.0.0/simgear/sound/jet.wav
SimGear-2.0.0/simgear/sound/Makefile.in
SimGear-2.0.0/simgear/sound/sample_openal.cxx
SimGear-2.0.0/simgear/sound/openal_test3.cxx
SimGear-2.0.0/simgear/sound/Makefile.am
SimGear-2.0.0/projects/
SimGear-2.0.0/projects/VC7.1/
SimGear-2.0.0/projects/VC7.1/SimGear.sln
SimGear-2.0.0/projects/VC7.1/.cvsignore
SimGear-2.0.0/projects/VC7.1/SimGear.vcproj
SimGear-2.0.0/projects/VC90/
SimGear-2.0.0/projects/VC90/.cvsignore
SimGear-2.0.0/projects/VC90/SimGear.vcproj
SimGear-2.0.0/config.sub
SimGear-2.0.0/README.OSG
SimGear-2.0.0/README.MSVC
SimGear-2.0.0/README.zlib
SimGear-2.0.0/install-sh
SimGear-2.0.0/config.guess
SimGear-2.0.0/Makefile.in
SimGear-2.0.0/SimGear.spec.in
SimGear-2.0.0/INSTALL
SimGear-2.0.0/configure.ac
SimGear-2.0.0/depcomp
SimGear-2.0.0/Makefile.am
SimGear-2.0.0/acinclude.m4
SimGear-2.0.0/aclocal.m4
SimGear-2.0.0/COPYING
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking CXX... 
checking CC... 
checking whether make sets $(MAKE)... (cached) yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c -p
checking whether ln -s works... yes
checking for boostlib >= 1.37.0... configure: error: We could not detect the boost libraries (version 1.37 or higher). If you have a staged boost library (still not installed) please specify $BOOST_ROOT in your environment and do not give a PATH to --with-boost option.  If you are sure you have boost installed, then check your version number looking in <boost/version.hpp>. See [http://randspringer.de/boost](http://randspringer.de/boost) for more documentation.
./downloadinstallfgrun.sh: line 27: cd: fgrun-1.5.2: No such file or directory
./downloadinstallfgrun.sh: line 28: ./configure: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
rm: cannot remove `download': No such file or directory
rm: cannot remove `fgrun-1.5.2': No such file or directory
rm: cannot remove `SimGear-2.0.0': No such file or directory
Installation complete.  You should now be able to open fgrun by typing the following command into a terminal: fgrun
If there were any errors, send me a PM, or reply to the thread.  I will try to get a fix in ASAP.
Enjoy!
mike@mike-GA-MA78LM-S2H:~/Downloads$ fgrun
No command 'fgrun' found, did you mean:
 Command 'fbrun' from package 'fluxbox' (universe)
 Command 'grun' from package 'grun' (universe)
fgrun: command not found
mike@mike-GA-MA78LM-S2H:~/Downloads$
```

---

### Post by ubudog on 2011-05-26
Everyone, try the new update.

[http://ubuntuforums.org/showthread.php?t=1672490](http://ubuntuforums.org/showthread.php?t=1672490)

Hope it works, let me know.  I'm about to start testing it myself...

---

### Post by 633Dh98 on 2011-05-27
Still no fgrun.

Do I need to place and bash downloadinstallfgrun.sh in a particular directory in order for it to work?

---

### Post by ubudog on 2011-05-27
Now that you mention it, I think you do.  Try placing the script in your home directory and running it.

---

### Post by ubudog on 2011-05-27
OK, I see the problem.  The script does not install one needed dependency.  I have fixed it (hopefully), and I'm about to upload it...

---

### Post by ubudog on 2011-05-27
Allrighty, new version is uploaded.  Check it out here:
[http://ubuntuforums.org/showthread.php?p=10381849#post10381849](http://ubuntuforums.org/showthread.php?p=10381849#post10381849)

Off to testing!

---

### Post by ubudog on 2011-05-27
OK, after testing, I can confirm that the script now works on a fresh install of Ubuntu 11.04.  Fgrun gets installed and I am able to run it with:
```
fgrun
```

To make sure it works, please be sure to:
1. Put the script in your home directory, and run it from there
2. Run it as a regular user

Hope it is fixed now, let me know if you still have problems.  :-)

---

### Post by lkjoel on 2011-05-28
> **wheresmything said:**
> i keep getting "permission denied"
to wit, 

james@Andromeda-II:~$ cd /home/james
james@Andromeda-II:~$ ./downloadinstallfgrun.sh
bash: ./downloadinstallfgrun.sh: Permission denied
james@Andromeda-II:~$ sudo su
[sudo] password for james: 
root@Andromeda-II:/home/james# ./downloadinstallfgrun.sh
bash: ./downloadinstallfgrun.sh: Permission denied

help?
Try this:
```
bash ./downloadinstallfgrun.sh

```

---

### Post by lkjoel on 2011-05-28
This script does not work if the user does not run it on $HOME.
I attached a patch.
To use it, copy and paste the patch to the directory where the script is, and type in:
```
patch downloadinstallfgrun.sh fix.txt

```

---

### Post by 633Dh98 on 2011-05-28
Still no go.

Downloaded most recent (May27) downloadinstallfgrun.sh, cut and pasted to home directory. 

Then  
mike@mike-GA-MA78LM-S2H:/home$ sudo ./downloadinstallfgrun.sh

File ran much longer than previous attempts but 

Installation complete.  You should now be able to open fgrun by typing the following command into a terminal: fgrun
If there were any errors, send me a PM, or reply to the thread.  I will try to get a fix in ASAP.
Enjoy!
mike@mike-GA-MA78LM-S2H:/home$ fgrun
No command 'fgrun' found, did you mean:
 Command 'fbrun' from package 'fluxbox' (universe)
 Command 'grun' from package 'grun' (universe)
fgrun: command not found

---

### Post by 633Dh98 on 2011-05-28
lkjoel,

Your patch did the trick.

Downloaded both downloadinstallfgrun.sh and fix.txt to home.  Patched then bashed the script.  Now fgrun works.

Thanks for everyones efforts.

---

### Post by ubudog on 2011-05-28
> **633Dh98 said:**
> Still no go.

Downloaded most recent (May27) downloadinstallfgrun.sh, cut and pasted to home directory. 

Then  
mike@mike-GA-MA78LM-S2H:/home$ sudo ./downloadinstallfgrun.sh

File ran much longer than previous attempts but 

Installation complete.  You should now be able to open fgrun by typing the following command into a terminal: fgrun
If there were any errors, send me a PM, or reply to the thread.  I will try to get a fix in ASAP.
Enjoy!
mike@mike-GA-MA78LM-S2H:/home$ fgrun
No command 'fgrun' found, did you mean:
 Command 'fbrun' from package 'fluxbox' (universe)
 Command 'grun' from package 'grun' (universe)
fgrun: command not found
EDIT: Now irrelevant.

---

### Post by ubudog on 2011-05-28
> **633Dh98 said:**
> lkjoel,

Your patch did the trick.

Downloaded both downloadinstallfgrun.sh and fix.txt to home.  Patched then bashed the script.  Now fgrun works.

Thanks for everyones efforts.

Great!  Glad you got it working, and thanks to Joel for that patch.  I will add it to the script.

---

### Post by lkjoel on 2011-05-28
> **ubudog said:**
> Great!  Glad you got it working, and thanks to Joel for that patch.  I will add it to the script.
Still, the patch is not excellent.
I have made another patch that will make it work even better.
Copy and paste the patch to where the script is, and type this in:
```
patch downloadinstallfgrun.sh fix2.txt

```

---

### Post by ubudog on 2011-06-26
Update: lkjoel's patch is now applied in the script, and the license has been changed to GNU GPL3.

---

### Post by stoast on 2011-07-21
I'm using 10.04 and I am pulling my hair out trying to get fgrun to work. Linux for human beings my ***! I am normally quite patient but I have hit so many brick wall today.

Please can someone give me some simple, straight forward steps to get a GUI interface(any one) for FligthGear to work!!!

---

### Post by lkjoel on 2011-07-21
> **stoast said:**
> I'm using 10.04 and I am pulling my hair out trying to get fgrun to work. Linux for human beings my ***! I am normally quite patient but I have hit so many brick wall today.

Please can someone give me some simple, straight forward steps to get a GUI interface(any one) for FligthGear to work!!!
[FONT=Verdana]Open up a Terminal window, and type in it:
[/FONT]```
svn co https://fgstartup.svn.sourceforge.net/svnroot/fgstartup fgstartup         	
sudo apt-get install qt4-dev-tools
qmake
make
./FGStartup

```

---

### Post by |{urse on 2011-07-21
> **633Dh98 said:**
> ```
mike@mike-GA-MA78LM-S2H:~/Downloads$ bash ./downloadinstallfgrun.sh
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libfltk1.1 is already the newest version.
libfltk1.1-dev is already the newest version.
zlib1g is already the newest version.
zlib1g-dev is already the newest version.
libalut-dev is already the newest version.
libalut0 is already the newest version.
libopenal-dev is already the newest version.
libopenal1 is already the newest version.
libplib-dev is already the newest version.
libplib1 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
--2011-05-25 15:50:36--  [http://sourceforge.net/projects/fgrun/files/fgrun/1.5.2/fgrun-1.5.2.tar.gz/download](http://sourceforge.net/projects/fgrun/files/fgrun/1.5.2/fgrun-1.5.2.tar.gz/download)
Resolving sourceforge.net... 216.34.181.60
Connecting to sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/project/fgrun/fgrun/1.5.2/fgrun-1.5.2.tar.gz?r=&ts=1306353040&use_mirror=surfnet](http://downloads.sourceforge.net/project/fgrun/fgrun/1.5.2/fgrun-1.5.2.tar.gz?r=&ts=1306353040&use_mirror=surfnet) [following]
--2011-05-25 15:50:41--  [http://downloads.sourceforge.net/project/fgrun/fgrun/1.5.2/fgrun-1.5.2.tar.gz?r=&ts=1306353040&use_mirror=surfnet](http://downloads.sourceforge.net/project/fgrun/fgrun/1.5.2/fgrun-1.5.2.tar.gz?r=&ts=1306353040&use_mirror=surfnet)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://surfnet.dl.sourceforge.net/project/fgrun/fgrun/1.5.2/fgrun-1.5.2.tar.gz](http://surfnet.dl.sourceforge.net/project/fgrun/fgrun/1.5.2/fgrun-1.5.2.tar.gz) [following]
--2011-05-25 15:50:41--  [http://surfnet.dl.sourceforge.net/project/fgrun/fgrun/1.5.2/fgrun-1.5.2.tar.gz](http://surfnet.dl.sourceforge.net/project/fgrun/fgrun/1.5.2/fgrun-1.5.2.tar.gz)
Resolving surfnet.dl.sourceforge.net... 130.59.138.21, 2001:620:0:1b::21
Connecting to surfnet.dl.sourceforge.net|130.59.138.21|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 386102 (377K) [application/x-gzip]
Saving to: `download'

100%[==========================================================================================>] 386,102      146K/s   in 2.6s    

2011-05-25 15:50:44 (146 KB/s) - `download' saved [386102/386102]

fgrun-1.5.2/
fgrun-1.5.2/m4/
fgrun-1.5.2/m4/lib-link.m4
fgrun-1.5.2/m4/po.m4
fgrun-1.5.2/m4/lib-ld.m4
fgrun-1.5.2/m4/iconv.m4
fgrun-1.5.2/m4/gettext.m4
fgrun-1.5.2/m4/nls.m4
fgrun-1.5.2/m4/progtest.m4
fgrun-1.5.2/m4/ChangeLog
fgrun-1.5.2/m4/lib-prefix.m4
fgrun-1.5.2/po/
fgrun-1.5.2/po/Makevars
fgrun-1.5.2/po/de.po
fgrun-1.5.2/po/es.po
fgrun-1.5.2/po/fr.po
fgrun-1.5.2/po/it.po
fgrun-1.5.2/po/LINGUAS
fgrun-1.5.2/po/nl.po
fgrun-1.5.2/po/pl.po
fgrun-1.5.2/po/pt.po
fgrun-1.5.2/po/en@boldquot.header
fgrun-1.5.2/po/en@quot.header
fgrun-1.5.2/po/Rules-quot
fgrun-1.5.2/po/remove-potcdate.sin
fgrun-1.5.2/po/boldquot.sed
fgrun-1.5.2/po/POTFILES.in
fgrun-1.5.2/po/de.gmo
fgrun-1.5.2/po/es.gmo
fgrun-1.5.2/po/fr.gmo
fgrun-1.5.2/po/it.gmo
fgrun-1.5.2/po/nl.gmo
fgrun-1.5.2/po/insert-header.sin
fgrun-1.5.2/po/pl.gmo
fgrun-1.5.2/po/pt.gmo
fgrun-1.5.2/po/stamp-po
fgrun-1.5.2/po/quot.sed
fgrun-1.5.2/po/ChangeLog
fgrun-1.5.2/po/Makefile.in.in
fgrun-1.5.2/po/fgrun.pot
fgrun-1.5.2/src/
fgrun-1.5.2/src/Fl_Table.cxx
fgrun-1.5.2/src/Fl_Table_Row.cxx
fgrun-1.5.2/src/os_win32.h
fgrun-1.5.2/src/fgrun_pty.cxx
fgrun-1.5.2/src/os_posix.h
fgrun-1.5.2/src/Fl_OSG.h
fgrun-1.5.2/src/AirportBrowser.cxx
fgrun-1.5.2/src/main.cxx
fgrun-1.5.2/src/advanced.cxx
fgrun-1.5.2/src/i18n.h
fgrun-1.5.2/src/AirportBrowser.h
fgrun-1.5.2/src/AirportTable.cxx
fgrun-1.5.2/src/Makefile.am
fgrun-1.5.2/src/Makefile.in
fgrun-1.5.2/src/io.cxx
fgrun-1.5.2/src/Fl_Table.H
fgrun-1.5.2/src/apt_dat.h
fgrun-1.5.2/src/Fl_Heading_Dial.H
fgrun-1.5.2/src/config.h.in
fgrun-1.5.2/src/Fl_OSG.cxx
fgrun-1.5.2/src/parkingloader.h
fgrun-1.5.2/src/settings.cxx
fgrun-1.5.2/src/Fl_Heading_Dial.cxx
fgrun-1.5.2/src/Fl_Table_Row.H
fgrun-1.5.2/src/util.h
fgrun-1.5.2/src/run_win32.cxx
fgrun-1.5.2/src/wizard.cxx
fgrun-1.5.2/src/AirportTable.h
fgrun-1.5.2/src/advanced.fl
fgrun-1.5.2/src/logwin.h
fgrun-1.5.2/src/wizard.fl
fgrun-1.5.2/src/wizard.h
fgrun-1.5.2/src/parkingloader.cxx
fgrun-1.5.2/src/fgfsrc.cxx
fgrun-1.5.2/src/run_posix.cxx
fgrun-1.5.2/src/advanced.h
fgrun-1.5.2/src/wizard_funcs.cxx
fgrun-1.5.2/src/fgrun_pty.h
fgrun-1.5.2/src/folder_open.xpm
fgrun-1.5.2/src/logwin.cxx
fgrun-1.5.2/src/util.cxx
fgrun-1.5.2/src/advanced_funcs.cxx
fgrun-1.5.2/NEWS
fgrun-1.5.2/msvc/
fgrun-1.5.2/msvc/6.0/
fgrun-1.5.2/msvc/6.0/fgrun.dsp
fgrun-1.5.2/msvc/6.0/fgrun.dsw
fgrun-1.5.2/msvc/7.1/
fgrun-1.5.2/msvc/7.1/fgrun.vcproj
fgrun-1.5.2/msvc/7.1/fgrun.sln
fgrun-1.5.2/depcomp
fgrun-1.5.2/aclocal.m4
fgrun-1.5.2/README
fgrun-1.5.2/configure
fgrun-1.5.2/fgrun.prefs
fgrun-1.5.2/configure.ac
fgrun-1.5.2/config.guess
fgrun-1.5.2/config.rpath
fgrun-1.5.2/install-sh
fgrun-1.5.2/autogen.sh
fgrun-1.5.2/config.sub
fgrun-1.5.2/missing
fgrun-1.5.2/Makefile.am
fgrun-1.5.2/Makefile.in
fgrun-1.5.2/acinclude.m4
fgrun-1.5.2/AUTHORS
fgrun-1.5.2/INSTALL
fgrun-1.5.2/ABOUT-NLS
fgrun-1.5.2/ChangeLog
fgrun-1.5.2/plib.m4
fgrun-1.5.2/COPYING
--2011-05-25 15:50:45--  [ftp://mirrors.ibiblio.org/pub/mirrors/simgear/ftp/Source/SimGear-2.0.0.tar.gz](ftp://mirrors.ibiblio.org/pub/mirrors/simgear/ftp/Source/SimGear-2.0.0.tar.gz)
           => `SimGear-2.0.0.tar.gz.1'
Resolving mirrors.ibiblio.org... 152.19.134.44
Connecting to mirrors.ibiblio.org|152.19.134.44|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD (1) /pub/mirrors/simgear/ftp/Source ... done.
==> SIZE SimGear-2.0.0.tar.gz ... 1058343
==> PASV ... done.    ==> RETR SimGear-2.0.0.tar.gz ... done.
Length: 1058343 (1.0M) (unauthoritative)

100%[==========================================================================================>] 1,058,343    228K/s   in 5.1s    

2011-05-25 15:50:50 (204 KB/s) - `SimGear-2.0.0.tar.gz.1' saved [1058343]

SimGear-2.0.0/
SimGear-2.0.0/README
SimGear-2.0.0/autogen.sh
SimGear-2.0.0/ChangeLog
SimGear-2.0.0/NEWS
SimGear-2.0.0/AUTHORS
SimGear-2.0.0/TODO
SimGear-2.0.0/DoxygenMain.cxx
SimGear-2.0.0/missing
SimGear-2.0.0/README.OpenAL
SimGear-2.0.0/configure
SimGear-2.0.0/README.plib
SimGear-2.0.0/simgear/
SimGear-2.0.0/simgear/version.h.in
SimGear-2.0.0/simgear/simgear_config.h-msvc71
SimGear-2.0.0/simgear/screen/
SimGear-2.0.0/simgear/screen/jpgfactory.cxx
SimGear-2.0.0/simgear/screen/win32-printer.h
SimGear-2.0.0/simgear/screen/extensions.cxx
SimGear-2.0.0/simgear/screen/GLBitmaps.cxx
SimGear-2.0.0/simgear/screen/RenderTexture.h
SimGear-2.0.0/simgear/screen/screen-dump.hxx
SimGear-2.0.0/simgear/screen/GLBitmaps.h
SimGear-2.0.0/simgear/screen/shader.h
SimGear-2.0.0/simgear/screen/jpgfactory.hxx
SimGear-2.0.0/simgear/screen/RenderTexture.cpp
SimGear-2.0.0/simgear/screen/tr.cxx
SimGear-2.0.0/simgear/screen/colors.hxx
SimGear-2.0.0/simgear/screen/extensions.hxx
SimGear-2.0.0/simgear/screen/TestRenderTexture.cpp
SimGear-2.0.0/simgear/screen/Makefile.in
SimGear-2.0.0/simgear/screen/shader.cpp
SimGear-2.0.0/simgear/screen/Makefile.am
SimGear-2.0.0/simgear/screen/screen-dump.cxx
SimGear-2.0.0/simgear/screen/tr.h
SimGear-2.0.0/simgear/misc/
SimGear-2.0.0/simgear/misc/texcoord.hxx
SimGear-2.0.0/simgear/misc/texcoord.cxx
SimGear-2.0.0/simgear/misc/interpolator.cxx
SimGear-2.0.0/simgear/misc/zfstream.cxx
SimGear-2.0.0/simgear/misc/PathOptions.hxx
SimGear-2.0.0/simgear/misc/sgstream.hxx
SimGear-2.0.0/simgear/misc/tabbed_values.cxx
SimGear-2.0.0/simgear/misc/strutils.hxx
SimGear-2.0.0/simgear/misc/stopwatch.hxx
SimGear-2.0.0/simgear/misc/interpolator.hxx
SimGear-2.0.0/simgear/misc/sg_path.cxx
SimGear-2.0.0/simgear/misc/stdint.hxx
SimGear-2.0.0/simgear/misc/tabbed_values.hxx
SimGear-2.0.0/simgear/misc/Makefile.in
SimGear-2.0.0/simgear/misc/sg_path.hxx
SimGear-2.0.0/simgear/misc/sgstream.cxx
SimGear-2.0.0/simgear/misc/strutils.cxx
SimGear-2.0.0/simgear/misc/Makefile.am
SimGear-2.0.0/simgear/misc/PathOptions.cxx
SimGear-2.0.0/simgear/misc/zfstream.hxx
SimGear-2.0.0/simgear/nasal/
SimGear-2.0.0/simgear/nasal/iolib.c
SimGear-2.0.0/simgear/nasal/bitslib.c
SimGear-2.0.0/simgear/nasal/nasal.h
SimGear-2.0.0/simgear/nasal/parse.c
SimGear-2.0.0/simgear/nasal/thread-win32.c
SimGear-2.0.0/simgear/nasal/gc.c
SimGear-2.0.0/simgear/nasal/code.c
SimGear-2.0.0/simgear/nasal/parse.h
SimGear-2.0.0/simgear/nasal/data.h
SimGear-2.0.0/simgear/nasal/mathlib.c
SimGear-2.0.0/simgear/nasal/iolib.h
SimGear-2.0.0/simgear/nasal/codegen.c
SimGear-2.0.0/simgear/nasal/string.c
SimGear-2.0.0/simgear/nasal/misc.c
SimGear-2.0.0/simgear/nasal/lib.c
SimGear-2.0.0/simgear/nasal/naref.h
SimGear-2.0.0/simgear/nasal/hash.c
SimGear-2.0.0/simgear/nasal/Makefile.in
SimGear-2.0.0/simgear/nasal/vector.c
SimGear-2.0.0/simgear/nasal/threadlib.c
SimGear-2.0.0/simgear/nasal/lex.c
SimGear-2.0.0/simgear/nasal/Makefile.am
SimGear-2.0.0/simgear/nasal/utf8lib.c
SimGear-2.0.0/simgear/nasal/thread-posix.c
SimGear-2.0.0/simgear/nasal/code.h
SimGear-2.0.0/simgear/debug/
SimGear-2.0.0/simgear/debug/logtest.cxx
SimGear-2.0.0/simgear/debug/debug_types.h
SimGear-2.0.0/simgear/debug/logstream.cxx
SimGear-2.0.0/simgear/debug/logstream.hxx
SimGear-2.0.0/simgear/debug/Makefile.in
SimGear-2.0.0/simgear/debug/Makefile.am
SimGear-2.0.0/simgear/compiler.h
SimGear-2.0.0/simgear/io/
SimGear-2.0.0/simgear/io/sg_socket_udp.cxx
SimGear-2.0.0/simgear/io/decode_binobj.cxx
SimGear-2.0.0/simgear/io/sg_binobj.cxx
SimGear-2.0.0/simgear/io/socktest.cxx
SimGear-2.0.0/simgear/io/sg_socket.hxx
SimGear-2.0.0/simgear/io/tcp_client.cxx
SimGear-2.0.0/simgear/io/sg_socket.cxx
SimGear-2.0.0/simgear/io/sg_file.hxx
SimGear-2.0.0/simgear/io/lowtest.cxx
SimGear-2.0.0/simgear/io/sg_socket_udp.hxx
SimGear-2.0.0/simgear/io/lowlevel.cxx
SimGear-2.0.0/simgear/io/sg_binobj.hxx
SimGear-2.0.0/simgear/io/lowlevel.hxx
SimGear-2.0.0/simgear/io/iochannel.hxx
SimGear-2.0.0/simgear/io/iochannel.cxx
SimGear-2.0.0/simgear/io/Makefile.in
SimGear-2.0.0/simgear/io/sg_serial.hxx
SimGear-2.0.0/simgear/io/sg_file.cxx
SimGear-2.0.0/simgear/io/Makefile.am
SimGear-2.0.0/simgear/io/tcp_server.cxx
SimGear-2.0.0/simgear/io/sg_serial.cxx
SimGear-2.0.0/simgear/compatibility/
SimGear-2.0.0/simgear/compatibility/MIPSpro721/
SimGear-2.0.0/simgear/compatibility/MIPSpro721/iostream
SimGear-2.0.0/simgear/compatibility/MIPSpro721/irix_string
SimGear-2.0.0/simgear/compatibility/MIPSpro721/sstream
SimGear-2.0.0/simgear/compatibility/MIPSpro721/istream
SimGear-2.0.0/simgear/compatibility/MIPSpro721/streambuf
SimGear-2.0.0/simgear/compatibility/MIPSpro721/iterator
SimGear-2.0.0/simgear/compatibility/MIPSpro721/new
SimGear-2.0.0/simgear/compatibility/MIPSpro721/iomanip
SimGear-2.0.0/simgear/compatibility/MIPSpro721/fstream
SimGear-2.0.0/simgear/compatibility/MIPSpro721/Makefile.in
SimGear-2.0.0/simgear/compatibility/MIPSpro721/Makefile.am
SimGear-2.0.0/simgear/compatibility/MIPSpro721/strstream
SimGear-2.0.0/simgear/compatibility/MIPSpro740/
SimGear-2.0.0/simgear/compatibility/MIPSpro740/cctype
SimGear-2.0.0/simgear/compatibility/MIPSpro740/README
SimGear-2.0.0/simgear/compatibility/MIPSpro740/clocale
SimGear-2.0.0/simgear/compatibility/MIPSpro740/cstring
SimGear-2.0.0/simgear/compatibility/MIPSpro740/ctime
SimGear-2.0.0/simgear/compatibility/MIPSpro740/cstddef
SimGear-2.0.0/simgear/compatibility/MIPSpro740/csetjmp
SimGear-2.0.0/simgear/compatibility/MIPSpro740/cstdio
SimGear-2.0.0/simgear/compatibility/MIPSpro740/cstdlib
SimGear-2.0.0/simgear/compatibility/MIPSpro740/cwchar
SimGear-2.0.0/simgear/compatibility/MIPSpro740/cstdarg
SimGear-2.0.0/simgear/compatibility/MIPSpro740/cassert
SimGear-2.0.0/simgear/compatibility/MIPSpro740/cfloat
SimGear-2.0.0/simgear/compatibility/MIPSpro740/cmath
SimGear-2.0.0/simgear/compatibility/MIPSpro740/cwctype
SimGear-2.0.0/simgear/compatibility/MIPSpro740/Makefile.in
SimGear-2.0.0/simgear/compatibility/MIPSpro740/cerrno
SimGear-2.0.0/simgear/compatibility/MIPSpro740/csignal
SimGear-2.0.0/simgear/compatibility/MIPSpro740/climits
SimGear-2.0.0/simgear/compatibility/MIPSpro740/Makefile.am
SimGear-2.0.0/simgear/compatibility/Makefile.in
SimGear-2.0.0/simgear/compatibility/Makefile.am
SimGear-2.0.0/simgear/props/
SimGear-2.0.0/simgear/props/props_test.cxx
SimGear-2.0.0/simgear/props/condition.hxx
SimGear-2.0.0/simgear/props/AtomicChangeListener.hxx
SimGear-2.0.0/simgear/props/ExtendedPropertyAdapter.hxx
SimGear-2.0.0/simgear/props/props.hxx
SimGear-2.0.0/simgear/props/AtomicChangeListener.cxx
SimGear-2.0.0/simgear/props/props_io.cxx
SimGear-2.0.0/simgear/props/props.cxx
SimGear-2.0.0/simgear/props/Makefile.in
SimGear-2.0.0/simgear/props/props_io.hxx
SimGear-2.0.0/simgear/props/condition.cxx
SimGear-2.0.0/simgear/props/Makefile.am
SimGear-2.0.0/simgear/xml/
SimGear-2.0.0/simgear/xml/utf8tab.h
SimGear-2.0.0/simgear/xml/iasciitab.h
SimGear-2.0.0/simgear/xml/easyxml.cxx
SimGear-2.0.0/simgear/xml/xmldef.h
SimGear-2.0.0/simgear/xml/xmlrole.h
SimGear-2.0.0/simgear/xml/asciitab.h
SimGear-2.0.0/simgear/xml/xmlrole.c
SimGear-2.0.0/simgear/xml/xmltok.c
SimGear-2.0.0/simgear/xml/xmltok_impl.h
SimGear-2.0.0/simgear/xml/xmlparse.h
SimGear-2.0.0/simgear/xml/hashtable.h
SimGear-2.0.0/simgear/xml/easyxml.hxx
SimGear-2.0.0/simgear/xml/xmltok_impl.c
SimGear-2.0.0/simgear/xml/latin1tab.h
SimGear-2.0.0/simgear/xml/nametab.h
SimGear-2.0.0/simgear/xml/xmltok.h
SimGear-2.0.0/simgear/xml/xmlparse.c
SimGear-2.0.0/simgear/xml/Makefile.in
SimGear-2.0.0/simgear/xml/Makefile.am
SimGear-2.0.0/simgear/xml/hashtable.c
SimGear-2.0.0/simgear/xml/xmltok_ns.c
SimGear-2.0.0/simgear/timing/
SimGear-2.0.0/simgear/timing/geocoord.cxx
SimGear-2.0.0/simgear/timing/timezone.h
SimGear-2.0.0/simgear/timing/sg_time.cxx
SimGear-2.0.0/simgear/timing/lowleveltime.h
SimGear-2.0.0/simgear/timing/timestamp.cxx
SimGear-2.0.0/simgear/timing/timestamp.hxx
SimGear-2.0.0/simgear/timing/lowleveltime.cxx
SimGear-2.0.0/simgear/timing/Makefile.in
SimGear-2.0.0/simgear/timing/sg_time.hxx
SimGear-2.0.0/simgear/timing/timezone.cxx
SimGear-2.0.0/simgear/timing/Makefile.am
SimGear-2.0.0/simgear/timing/geocoord.h
SimGear-2.0.0/simgear/simgear_config.h.in
SimGear-2.0.0/simgear/bucket/
SimGear-2.0.0/simgear/bucket/newbucket.hxx
SimGear-2.0.0/simgear/bucket/newbucket.cxx
SimGear-2.0.0/simgear/bucket/Makefile.in
SimGear-2.0.0/simgear/bucket/Makefile.am
SimGear-2.0.0/simgear/route/
SimGear-2.0.0/simgear/route/routetest.cxx
SimGear-2.0.0/simgear/route/waypoint.cxx
SimGear-2.0.0/simgear/route/waypoint.hxx
SimGear-2.0.0/simgear/route/route.hxx
SimGear-2.0.0/simgear/route/Makefile.in
SimGear-2.0.0/simgear/route/waytest.cxx
SimGear-2.0.0/simgear/route/route.cxx
SimGear-2.0.0/simgear/route/Makefile.am
SimGear-2.0.0/simgear/threads/
SimGear-2.0.0/simgear/threads/SGQueue.hxx
SimGear-2.0.0/simgear/threads/SGThread.hxx
SimGear-2.0.0/simgear/threads/Makefile.in
SimGear-2.0.0/simgear/threads/SGGuard.hxx
SimGear-2.0.0/simgear/threads/SGThread.cxx
SimGear-2.0.0/simgear/threads/Makefile.am
SimGear-2.0.0/simgear/simgear_config.h.vc5
SimGear-2.0.0/simgear/ephemeris/
SimGear-2.0.0/simgear/ephemeris/mars.cxx
SimGear-2.0.0/simgear/ephemeris/venus.cxx
SimGear-2.0.0/simgear/ephemeris/moonpos.cxx
SimGear-2.0.0/simgear/ephemeris/venus.hxx
SimGear-2.0.0/simgear/ephemeris/jupiter.hxx
SimGear-2.0.0/simgear/ephemeris/pluto.hxx
SimGear-2.0.0/simgear/ephemeris/jupiter.cxx
SimGear-2.0.0/simgear/ephemeris/ephemeris.hxx
SimGear-2.0.0/simgear/ephemeris/saturn.hxx
SimGear-2.0.0/simgear/ephemeris/saturn.cxx
SimGear-2.0.0/simgear/ephemeris/uranus.cxx
SimGear-2.0.0/simgear/ephemeris/celestialBody.hxx
SimGear-2.0.0/simgear/ephemeris/stardata.cxx
SimGear-2.0.0/simgear/ephemeris/moonpos.hxx
SimGear-2.0.0/simgear/ephemeris/stardata.hxx
SimGear-2.0.0/simgear/ephemeris/mercury.hxx
SimGear-2.0.0/simgear/ephemeris/mars.hxx
SimGear-2.0.0/simgear/ephemeris/neptune.hxx
SimGear-2.0.0/simgear/ephemeris/neptune.cxx
SimGear-2.0.0/simgear/ephemeris/Makefile.in
SimGear-2.0.0/simgear/ephemeris/ephemeris.cxx
SimGear-2.0.0/simgear/ephemeris/mercury.cxx
SimGear-2.0.0/simgear/ephemeris/star.cxx
SimGear-2.0.0/simgear/ephemeris/Makefile.am
SimGear-2.0.0/simgear/ephemeris/star.hxx
SimGear-2.0.0/simgear/ephemeris/uranus.hxx
SimGear-2.0.0/simgear/ephemeris/celestialBody.cxx
SimGear-2.0.0/simgear/structure/
SimGear-2.0.0/simgear/structure/OSGUtils.hxx
SimGear-2.0.0/simgear/structure/SGBinding.cxx
SimGear-2.0.0/simgear/structure/commands.cxx
SimGear-2.0.0/simgear/structure/event_mgr.hxx
SimGear-2.0.0/simgear/structure/SGSmplhist.cxx
SimGear-2.0.0/simgear/structure/SGSharedPtr.hxx
SimGear-2.0.0/simgear/structure/StringTable.hxx
SimGear-2.0.0/simgear/structure/SGSmplhist.hxx
SimGear-2.0.0/simgear/structure/SGExpression.cxx
SimGear-2.0.0/simgear/structure/event_mgr.cxx
SimGear-2.0.0/simgear/structure/intern.hxx
SimGear-2.0.0/simgear/structure/SGSmplstat.hxx
SimGear-2.0.0/simgear/structure/Singleton.hxx
SimGear-2.0.0/simgear/structure/SGWeakReferenced.hxx
SimGear-2.0.0/simgear/structure/commands.hxx
SimGear-2.0.0/simgear/structure/StringTable.cxx
SimGear-2.0.0/simgear/structure/SGExpression.hxx
SimGear-2.0.0/simgear/structure/exception.cxx
SimGear-2.0.0/simgear/structure/SGAtomic.hxx
SimGear-2.0.0/simgear/structure/SGAtomic.cxx
SimGear-2.0.0/simgear/structure/SGWeakPtr.hxx
SimGear-2.0.0/simgear/structure/SGSmplstat.cxx
SimGear-2.0.0/simgear/structure/callback.hxx
SimGear-2.0.0/simgear/structure/Makefile.in
SimGear-2.0.0/simgear/structure/subsystem_mgr.hxx
SimGear-2.0.0/simgear/structure/SGReferenced.hxx
SimGear-2.0.0/simgear/structure/Makefile.am
SimGear-2.0.0/simgear/structure/OSGVersion.hxx
SimGear-2.0.0/simgear/structure/subsystem_mgr.cxx
SimGear-2.0.0/simgear/structure/exception.hxx
SimGear-2.0.0/simgear/structure/SGBinding.hxx
SimGear-2.0.0/simgear/version.h
SimGear-2.0.0/simgear/constants.h
SimGear-2.0.0/simgear/scene/
SimGear-2.0.0/simgear/scene/tgdb/
SimGear-2.0.0/simgear/scene/tgdb/ReaderWriterSTG.hxx
SimGear-2.0.0/simgear/scene/tgdb/SGVertexArrayBin.hxx
SimGear-2.0.0/simgear/scene/tgdb/apt_signs.cxx
SimGear-2.0.0/simgear/scene/tgdb/SGTexturedTriangleBin.hxx
SimGear-2.0.0/simgear/scene/tgdb/TileCache.cxx
SimGear-2.0.0/simgear/scene/tgdb/SGVasiDrawable.hxx
SimGear-2.0.0/simgear/scene/tgdb/GroundLightManager.hxx
SimGear-2.0.0/simgear/scene/tgdb/userdata.hxx
SimGear-2.0.0/simgear/scene/tgdb/TreeBin.hxx
SimGear-2.0.0/simgear/scene/tgdb/pt_lights.hxx
SimGear-2.0.0/simgear/scene/tgdb/SGOceanTile.hxx
SimGear-2.0.0/simgear/scene/tgdb/apt_signs.hxx
SimGear-2.0.0/simgear/scene/tgdb/TileEntry.cxx
SimGear-2.0.0/simgear/scene/tgdb/TreeBin.cxx
SimGear-2.0.0/simgear/scene/tgdb/SGReaderWriterBTGOptions.hxx
SimGear-2.0.0/simgear/scene/tgdb/SGTriangleBin.hxx
SimGear-2.0.0/simgear/scene/tgdb/ShaderGeometry.cxx
SimGear-2.0.0/simgear/scene/tgdb/pt_lights.cxx
SimGear-2.0.0/simgear/scene/tgdb/SGVasiDrawable.cxx
SimGear-2.0.0/simgear/scene/tgdb/obj.cxx
SimGear-2.0.0/simgear/scene/tgdb/ReaderWriterSTG.cxx
SimGear-2.0.0/simgear/scene/tgdb/TileEntry.hxx
SimGear-2.0.0/simgear/scene/tgdb/SGLightBin.hxx
SimGear-2.0.0/simgear/scene/tgdb/ShaderGeometry.hxx
SimGear-2.0.0/simgear/scene/tgdb/SGReaderWriterBTG.hxx
SimGear-2.0.0/simgear/scene/tgdb/GroundLightManager.cxx
SimGear-2.0.0/simgear/scene/tgdb/obj.hxx
SimGear-2.0.0/simgear/scene/tgdb/TileCache.hxx
SimGear-2.0.0/simgear/scene/tgdb/SGModelBin.hxx
SimGear-2.0.0/simgear/scene/tgdb/userdata.cxx
SimGear-2.0.0/simgear/scene/tgdb/Makefile.in
SimGear-2.0.0/simgear/scene/tgdb/SGReaderWriterBTG.cxx
SimGear-2.0.0/simgear/scene/tgdb/SGDirectionalLightBin.hxx
SimGear-2.0.0/simgear/scene/tgdb/Makefile.am
SimGear-2.0.0/simgear/scene/tgdb/SGOceanTile.cxx
SimGear-2.0.0/simgear/scene/model/
SimGear-2.0.0/simgear/scene/model/SGMaterialAnimation.cxx
SimGear-2.0.0/simgear/scene/model/shadanim.cxx
SimGear-2.0.0/simgear/scene/model/model.cxx
SimGear-2.0.0/simgear/scene/model/ModelRegistry.cxx
SimGear-2.0.0/simgear/scene/model/SGInteractionAnimation.cxx
SimGear-2.0.0/simgear/scene/model/BoundingVolumeBuildVisitor.hxx
SimGear-2.0.0/simgear/scene/model/persparam.cxx
SimGear-2.0.0/simgear/scene/model/SGInteractionAnimation.hxx
SimGear-2.0.0/simgear/scene/model/modellib.cxx
SimGear-2.0.0/simgear/scene/model/SGOffsetTransform.cxx
SimGear-2.0.0/simgear/scene/model/SGPagedLOD.hxx
SimGear-2.0.0/simgear/scene/model/SGRotateTransform.hxx
SimGear-2.0.0/simgear/scene/model/particles.cxx
SimGear-2.0.0/simgear/scene/model/SGMaterialAnimation.hxx
SimGear-2.0.0/simgear/scene/model/SGReaderWriterXMLOptions.hxx
SimGear-2.0.0/simgear/scene/model/CheckSceneryVisitor.hxx
SimGear-2.0.0/simgear/scene/model/particles.hxx
SimGear-2.0.0/simgear/scene/model/SGText.cxx
SimGear-2.0.0/simgear/scene/model/SGText.hxx
SimGear-2.0.0/simgear/scene/model/SGOffsetTransform.hxx
SimGear-2.0.0/simgear/scene/model/SGReaderWriterXML.cxx
SimGear-2.0.0/simgear/scene/model/SGClipGroup.hxx
SimGear-2.0.0/simgear/scene/model/animation.cxx
SimGear-2.0.0/simgear/scene/model/SGReaderWriterXML.hxx
SimGear-2.0.0/simgear/scene/model/placement.cxx
SimGear-2.0.0/simgear/scene/model/SGTranslateTransform.hxx
SimGear-2.0.0/simgear/scene/model/persparam.hxx
SimGear-2.0.0/simgear/scene/model/CheckSceneryVisitor.cxx
SimGear-2.0.0/simgear/scene/model/SGScaleTransform.cxx
SimGear-2.0.0/simgear/scene/model/SGRotateTransform.cxx
SimGear-2.0.0/simgear/scene/model/SGTranslateTransform.cxx
SimGear-2.0.0/simgear/scene/model/Makefile.in
SimGear-2.0.0/simgear/scene/model/SGClipGroup.cxx
SimGear-2.0.0/simgear/scene/model/animation.hxx
SimGear-2.0.0/simgear/scene/model/SGScaleTransform.hxx
SimGear-2.0.0/simgear/scene/model/placement.hxx
SimGear-2.0.0/simgear/scene/model/SGPagedLOD.cxx
SimGear-2.0.0/simgear/scene/model/modellib.hxx
SimGear-2.0.0/simgear/scene/model/Makefile.am
SimGear-2.0.0/simgear/scene/model/ModelRegistry.hxx
SimGear-2.0.0/simgear/scene/model/model.hxx
SimGear-2.0.0/simgear/scene/util/
SimGear-2.0.0/simgear/scene/util/UpdateOnceCallback.hxx
SimGear-2.0.0/simgear/scene/util/QuadTreeBuilder.cxx
SimGear-2.0.0/simgear/scene/util/SGSceneUserData.cxx
SimGear-2.0.0/simgear/scene/util/SGTextureStateAttributeVisitor.hxx
SimGear-2.0.0/simgear/scene/util/SplicingVisitor.cxx
SimGear-2.0.0/simgear/scene/util/PrimitiveUtils.cxx
SimGear-2.0.0/simgear/scene/util/SGEnlargeBoundingBox.hxx
SimGear-2.0.0/simgear/scene/util/QuadTreeBuilder.hxx
SimGear-2.0.0/simgear/scene/util/SGDebugDrawCallback.hxx
SimGear-2.0.0/simgear/scene/util/NodeAndDrawableVisitor.hxx
SimGear-2.0.0/simgear/scene/util/RenderConstants.hxx
SimGear-2.0.0/simgear/scene/util/SGUpdateVisitor.hxx
SimGear-2.0.0/simgear/scene/util/CopyOp.hxx
SimGear-2.0.0/simgear/scene/util/PrimitiveUtils.hxx
SimGear-2.0.0/simgear/scene/util/StateAttributeFactory.hxx
SimGear-2.0.0/simgear/scene/util/StateAttributeFactory.cxx
SimGear-2.0.0/simgear/scene/util/SGPickCallback.hxx
SimGear-2.0.0/simgear/scene/util/SGStateAttributeVisitor.cxx
SimGear-2.0.0/simgear/scene/util/VectorArrayAdapter.hxx
SimGear-2.0.0/simgear/scene/util/SGSceneFeatures.hxx
SimGear-2.0.0/simgear/scene/util/SGStateAttributeVisitor.hxx
SimGear-2.0.0/simgear/scene/util/SGSceneUserData.hxx
SimGear-2.0.0/simgear/scene/util/SGTextureStateAttributeVisitor.cxx
SimGear-2.0.0/simgear/scene/util/UpdateOnceCallback.cxx
SimGear-2.0.0/simgear/scene/util/SGSceneFeatures.cxx
SimGear-2.0.0/simgear/scene/util/SGEnlargeBoundingBox.cxx
SimGear-2.0.0/simgear/scene/util/SplicingVisitor.hxx
SimGear-2.0.0/simgear/scene/util/Makefile.in
SimGear-2.0.0/simgear/scene/util/NodeAndDrawableVisitor.cxx
SimGear-2.0.0/simgear/scene/util/SGNodeMasks.hxx
SimGear-2.0.0/simgear/scene/util/CopyOp.cxx
SimGear-2.0.0/simgear/scene/util/Makefile.am
SimGear-2.0.0/simgear/scene/material/
SimGear-2.0.0/simgear/scene/material/matmodel.hxx
SimGear-2.0.0/simgear/scene/material/matlib.hxx
SimGear-2.0.0/simgear/scene/material/Pass.hxx
SimGear-2.0.0/simgear/scene/material/GLPredicate.hxx
SimGear-2.0.0/simgear/scene/material/TextureBuilder.cxx
SimGear-2.0.0/simgear/scene/material/matmodel.cxx
SimGear-2.0.0/simgear/scene/material/Technique.hxx
SimGear-2.0.0/simgear/scene/material/EffectGeode.hxx
SimGear-2.0.0/simgear/scene/material/EffectGeode.cxx
SimGear-2.0.0/simgear/scene/material/TextureBuilder.hxx
SimGear-2.0.0/simgear/scene/material/EffectBuilder.cxx
SimGear-2.0.0/simgear/scene/material/mat.hxx
SimGear-2.0.0/simgear/scene/material/Noise.cxx
SimGear-2.0.0/simgear/scene/material/EffectCullVisitor.cxx
SimGear-2.0.0/simgear/scene/material/matlib.cxx
SimGear-2.0.0/simgear/scene/material/GLPredicate.cxx
SimGear-2.0.0/simgear/scene/material/mat.cxx
SimGear-2.0.0/simgear/scene/material/Technique.cxx
SimGear-2.0.0/simgear/scene/material/EffectCullVisitor.hxx
SimGear-2.0.0/simgear/scene/material/Pass.cxx
SimGear-2.0.0/simgear/scene/material/Effect.hxx
SimGear-2.0.0/simgear/scene/material/makeEffect.cxx
SimGear-2.0.0/simgear/scene/material/Makefile.in
SimGear-2.0.0/simgear/scene/material/EffectBuilder.hxx
SimGear-2.0.0/simgear/scene/material/Makefile.am
SimGear-2.0.0/simgear/scene/material/Effect.cxx
SimGear-2.0.0/simgear/scene/material/Noise.hxx
SimGear-2.0.0/simgear/scene/sky/
SimGear-2.0.0/simgear/scene/sky/dome.hxx
SimGear-2.0.0/simgear/scene/sky/cloud.cxx
SimGear-2.0.0/simgear/scene/sky/moon.hxx
SimGear-2.0.0/simgear/scene/sky/bbcache.hxx
SimGear-2.0.0/simgear/scene/sky/oursun.cxx
SimGear-2.0.0/simgear/scene/sky/oursun.hxx
SimGear-2.0.0/simgear/scene/sky/cloudfield.hxx
SimGear-2.0.0/simgear/scene/sky/newcloud.cxx
SimGear-2.0.0/simgear/scene/sky/dome.cxx
SimGear-2.0.0/simgear/scene/sky/stars.cxx
SimGear-2.0.0/simgear/scene/sky/bbcache.cxx
SimGear-2.0.0/simgear/scene/sky/newcloud.hxx
SimGear-2.0.0/simgear/scene/sky/sky.cxx
SimGear-2.0.0/simgear/scene/sky/Makefile.in
SimGear-2.0.0/simgear/scene/sky/sky.hxx
SimGear-2.0.0/simgear/scene/sky/CloudShaderGeometry.cxx
SimGear-2.0.0/simgear/scene/sky/cloudfield.cxx
SimGear-2.0.0/simgear/scene/sky/Makefile.am
SimGear-2.0.0/simgear/scene/sky/moon.cxx
SimGear-2.0.0/simgear/scene/sky/sphere.hxx
SimGear-2.0.0/simgear/scene/sky/cloud.hxx
SimGear-2.0.0/simgear/scene/sky/stars.hxx
SimGear-2.0.0/simgear/scene/sky/sphere.cxx
SimGear-2.0.0/simgear/scene/sky/CloudShaderGeometry.hxx
SimGear-2.0.0/simgear/scene/bvh/
SimGear-2.0.0/simgear/scene/bvh/BVHLineSegmentVisitor.cxx
SimGear-2.0.0/simgear/scene/bvh/BVHNode.hxx
SimGear-2.0.0/simgear/scene/bvh/BVHStaticData.hxx
SimGear-2.0.0/simgear/scene/bvh/BVHDebugCollectVisitor.hxx
SimGear-2.0.0/simgear/scene/bvh/BVHLineGeometry.cxx
SimGear-2.0.0/simgear/scene/bvh/BVHStaticLeaf.hxx
SimGear-2.0.0/simgear/scene/bvh/BVHTransform.cxx
SimGear-2.0.0/simgear/scene/bvh/BVHStaticGeometryBuilder.hxx
SimGear-2.0.0/simgear/scene/bvh/BVHStaticGeometry.hxx
SimGear-2.0.0/simgear/scene/bvh/BVHMotionTransform.cxx
SimGear-2.0.0/simgear/scene/bvh/BVHGroup.cxx
SimGear-2.0.0/simgear/scene/bvh/bvhtest.cxx
SimGear-2.0.0/simgear/scene/bvh/BVHBoundingBoxVisitor.hxx
SimGear-2.0.0/simgear/scene/bvh/BVHSubTreeCollector.hxx
SimGear-2.0.0/simgear/scene/bvh/BVHStaticLeaf.cxx
SimGear-2.0.0/simgear/scene/bvh/BVHMotionTransform.hxx
SimGear-2.0.0/simgear/scene/bvh/BVHStaticNode.hxx
SimGear-2.0.0/simgear/scene/bvh/BVHStaticBinary.hxx
SimGear-2.0.0/simgear/scene/bvh/BVHLineGeometry.hxx
SimGear-2.0.0/simgear/scene/bvh/BVHSubTreeCollector.cxx
SimGear-2.0.0/simgear/scene/bvh/BVHStaticNode.cxx
SimGear-2.0.0/simgear/scene/bvh/BVHVisitor.hxx
SimGear-2.0.0/simgear/scene/bvh/BVHStaticBinary.cxx
SimGear-2.0.0/simgear/scene/bvh/BVHTransform.hxx
SimGear-2.0.0/simgear/scene/bvh/BVHLineSegmentVisitor.hxx
SimGear-2.0.0/simgear/scene/bvh/BVHStaticTriangle.hxx
SimGear-2.0.0/simgear/scene/bvh/BVHNearestPointVisitor.hxx
SimGear-2.0.0/simgear/scene/bvh/Makefile.in
SimGear-2.0.0/simgear/scene/bvh/BVHStaticGeometry.cxx
SimGear-2.0.0/simgear/scene/bvh/BVHNode.cxx
SimGear-2.0.0/simgear/scene/bvh/BVHGroup.hxx
SimGear-2.0.0/simgear/scene/bvh/Makefile.am
SimGear-2.0.0/simgear/scene/bvh/BVHStaticTriangle.cxx
SimGear-2.0.0/simgear/scene/Makefile.in
SimGear-2.0.0/simgear/scene/Makefile.am
SimGear-2.0.0/simgear/serial/
SimGear-2.0.0/simgear/serial/serial.cxx
SimGear-2.0.0/simgear/serial/serial.hxx
SimGear-2.0.0/simgear/serial/testserial.cxx
SimGear-2.0.0/simgear/serial/Makefile.in
SimGear-2.0.0/simgear/serial/Makefile.am
SimGear-2.0.0/simgear/Makefile.in
SimGear-2.0.0/simgear/environment/
SimGear-2.0.0/simgear/environment/metar.hxx
SimGear-2.0.0/simgear/environment/precipitation.cxx
SimGear-2.0.0/simgear/environment/metar.cxx
SimGear-2.0.0/simgear/environment/visual_enviro.cxx
SimGear-2.0.0/simgear/environment/visual_enviro.hxx
SimGear-2.0.0/simgear/environment/Makefile.in
SimGear-2.0.0/simgear/environment/precipitation.hxx
SimGear-2.0.0/simgear/environment/Makefile.am
SimGear-2.0.0/simgear/magvar/
SimGear-2.0.0/simgear/magvar/magvar.cxx
SimGear-2.0.0/simgear/magvar/coremag.cxx
SimGear-2.0.0/simgear/magvar/testmagvar.cxx
SimGear-2.0.0/simgear/magvar/Makefile.in
SimGear-2.0.0/simgear/magvar/magvar.hxx
SimGear-2.0.0/simgear/magvar/coremag.hxx
SimGear-2.0.0/simgear/magvar/Makefile.am
SimGear-2.0.0/simgear/sg_inlines.h
SimGear-2.0.0/simgear/Makefile.am
SimGear-2.0.0/simgear/math/
SimGear-2.0.0/simgear/math/SGMisc.hxx
SimGear-2.0.0/simgear/math/SGRay.hxx
SimGear-2.0.0/simgear/math/sg_geodesy.hxx
SimGear-2.0.0/simgear/math/SGGeodesy.cxx
SimGear-2.0.0/simgear/math/point3d.hxx
SimGear-2.0.0/simgear/math/SGGeometryFwd.hxx
SimGear-2.0.0/simgear/math/SGMathFwd.hxx
SimGear-2.0.0/simgear/math/Math.hxx
SimGear-2.0.0/simgear/math/beziercurve.hxx
SimGear-2.0.0/simgear/math/SGGeodesy.hxx
SimGear-2.0.0/simgear/math/SGBox.hxx
SimGear-2.0.0/simgear/math/SGSphere.hxx
SimGear-2.0.0/simgear/math/SGMathTest.cxx
SimGear-2.0.0/simgear/math/SGCMath.hxx
SimGear-2.0.0/simgear/math/SGPlane.hxx
SimGear-2.0.0/simgear/math/SGIntersect.hxx
SimGear-2.0.0/simgear/math/sg_types.hxx
SimGear-2.0.0/simgear/math/SGTriangle.hxx
SimGear-2.0.0/simgear/math/sg_random.c
SimGear-2.0.0/simgear/math/sg_random.h
SimGear-2.0.0/simgear/math/vector.hxx
SimGear-2.0.0/simgear/math/SGLimits.hxx
SimGear-2.0.0/simgear/math/SGGeometryTest.cxx
SimGear-2.0.0/simgear/math/leastsqs.cxx
SimGear-2.0.0/simgear/math/SGGeod.cxx
SimGear-2.0.0/simgear/math/SGQuat.hxx
SimGear-2.0.0/simgear/math/vector.cxx
SimGear-2.0.0/simgear/math/SGVec2.hxx
SimGear-2.0.0/simgear/math/interpolater.cxx
SimGear-2.0.0/simgear/math/SGMatrix.hxx
SimGear-2.0.0/simgear/math/interpolater.hxx
SimGear-2.0.0/simgear/math/leastsqs.hxx
SimGear-2.0.0/simgear/math/SGVec4.hxx
SimGear-2.0.0/simgear/math/SGVec3.hxx
SimGear-2.0.0/simgear/math/Makefile.in
SimGear-2.0.0/simgear/math/SGGeoc.hxx
SimGear-2.0.0/simgear/math/SGMath.hxx
SimGear-2.0.0/simgear/math/SGGeometry.hxx
SimGear-2.0.0/simgear/math/SGLineSegment.hxx
SimGear-2.0.0/simgear/math/Makefile.am
SimGear-2.0.0/simgear/math/SGGeod.hxx
SimGear-2.0.0/simgear/math/polar3d.hxx
SimGear-2.0.0/simgear/sound/
SimGear-2.0.0/simgear/sound/README
SimGear-2.0.0/simgear/sound/soundmgr_openal.cxx
SimGear-2.0.0/simgear/sound/xmlsound.cxx
SimGear-2.0.0/simgear/sound/sample_group.hxx
SimGear-2.0.0/simgear/sound/openal_test1.cxx
SimGear-2.0.0/simgear/sound/soundmgr_openal.hxx
SimGear-2.0.0/simgear/sound/openal_test2.cxx
SimGear-2.0.0/simgear/sound/sample_openal.hxx
SimGear-2.0.0/simgear/sound/sample_group.cxx
SimGear-2.0.0/simgear/sound/xmlsound.hxx
SimGear-2.0.0/simgear/sound/jet.wav
SimGear-2.0.0/simgear/sound/Makefile.in
SimGear-2.0.0/simgear/sound/sample_openal.cxx
SimGear-2.0.0/simgear/sound/openal_test3.cxx
SimGear-2.0.0/simgear/sound/Makefile.am
SimGear-2.0.0/projects/
SimGear-2.0.0/projects/VC7.1/
SimGear-2.0.0/projects/VC7.1/SimGear.sln
SimGear-2.0.0/projects/VC7.1/.cvsignore
SimGear-2.0.0/projects/VC7.1/SimGear.vcproj
SimGear-2.0.0/projects/VC90/
SimGear-2.0.0/projects/VC90/.cvsignore
SimGear-2.0.0/projects/VC90/SimGear.vcproj
SimGear-2.0.0/config.sub
SimGear-2.0.0/README.OSG
SimGear-2.0.0/README.MSVC
SimGear-2.0.0/README.zlib
SimGear-2.0.0/install-sh
SimGear-2.0.0/config.guess
SimGear-2.0.0/Makefile.in
SimGear-2.0.0/SimGear.spec.in
SimGear-2.0.0/INSTALL
SimGear-2.0.0/configure.ac
SimGear-2.0.0/depcomp
SimGear-2.0.0/Makefile.am
SimGear-2.0.0/acinclude.m4
SimGear-2.0.0/aclocal.m4
SimGear-2.0.0/COPYING
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking CXX... 
checking CC... 
checking whether make sets $(MAKE)... (cached) yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c -p
checking whether ln -s works... yes
checking for boostlib >= 1.37.0... configure: error: We could not detect the boost libraries (version 1.37 or higher). If you have a staged boost library (still not installed) please specify $BOOST_ROOT in your environment and do not give a PATH to --with-boost option.  If you are sure you have boost installed, then check your version number looking in <boost/version.hpp>. See [http://randspringer.de/boost](http://randspringer.de/boost) for more documentation.
./downloadinstallfgrun.sh: line 27: cd: fgrun-1.5.2: No such file or directory
./downloadinstallfgrun.sh: line 28: ./configure: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
rm: cannot remove `download': No such file or directory
rm: cannot remove `fgrun-1.5.2': No such file or directory
rm: cannot remove `SimGear-2.0.0': No such file or directory
Installation complete.  You should now be able to open fgrun by typing the following command into a terminal: fgrun
If there were any errors, send me a PM, or reply to the thread.  I will try to get a fix in ASAP.
Enjoy!
mike@mike-GA-MA78LM-S2H:~/Downloads$ fgrun
No command 'fgrun' found, did you mean:
 Command 'fbrun' from package 'fluxbox' (universe)
 Command 'grun' from package 'grun' (universe)
fgrun: command not found
mike@mike-GA-MA78LM-S2H:~/Downloads$
```

you need to

sudo apt-get install libboost-dev libboost-doc

---

### Post by emarkay on 2011-07-26
And it really needs all of these files just to install fgrun???   

libopenal1 is already the newest version.
libopenal1 set to manually installed.
libalut0 is already the newest version.
libalut0 set to manually installed.
libplib1 is already the newest version.
libplib1 set to manually installed.
zlib1g is already the newest version.
The following extra packages will be installed:
  freeglut3-dev gccxml libboost-date-time1.42-dev libboost-date-time1.42.0
  libboost-filesystem1.42-dev libboost-filesystem1.42.0 libboost-graph1.42-dev
  libboost-graph1.42.0 libboost-iostreams1.42-dev libboost-iostreams1.42.0
  libboost-math1.42-dev libboost-math1.42.0 libboost-program-options1.42-dev
  libboost-program-options1.42.0 libboost-python1.42-dev libboost-python1.42.0
  libboost-regex1.42-dev libboost-regex1.42.0 libboost-serialization1.42-dev
  libboost-serialization1.42.0 libboost-signals1.42-dev libboost-signals1.42.0
  libboost-system1.42-dev libboost-system1.42.0 libboost-test1.42-dev
  libboost-test1.42.0 libboost-thread1.42-dev libboost-thread1.42.0
  libboost-wave1.42-dev libboost-wave1.42.0 libboost1.42-dev libdrm-dev
  libgl1-mesa-dev libglu1-mesa-dev libice-dev libicu-dev libopenscenegraph-dev
  libopenthreads-dev libpthread-stubs0 libpthread-stubs0-dev libsm-dev
  libx11-dev libxau-dev libxcb1-dev libxdmcp-dev libxext-dev libxt-dev
  mesa-common-dev python-dev python2.6-dev x11proto-core-dev
  x11proto-input-dev x11proto-kb-dev x11proto-xext-dev xtrans-dev
Suggested packages:
  graphviz libboost1.42-doc doxygen docbook-xsl default-jdk fop fltk1.1-doc
  fluid libjpeg62-dev libpng12-0-dev libxft-dev libxinerama-dev icu-doc
.........
0 upgraded, 63 newly installed, 0 to remove and 1 not upgraded.
Need to get 36.2MB of archives.
After this operation, 164MB of additional disk space will be used."

Anyway, thanks for helping out those of us who aren't into compiling and dependency investigation...  :)

Looks like it's working - Note that I did not get any "finished" indication - after the script ran, Terminal just blinked off.
You should even add a desktop start icon for us lazy folks too.

---

### Post by ubudog on 2011-07-26
> **emarkay said:**
> And it really needs all of these files just to install fgrun???   

libopenal1 is already the newest version.
libopenal1 set to manually installed.
libalut0 is already the newest version.
libalut0 set to manually installed.
libplib1 is already the newest version.
libplib1 set to manually installed.
zlib1g is already the newest version.
The following extra packages will be installed:
  freeglut3-dev gccxml libboost-date-time1.42-dev libboost-date-time1.42.0
  libboost-filesystem1.42-dev libboost-filesystem1.42.0 libboost-graph1.42-dev
  libboost-graph1.42.0 libboost-iostreams1.42-dev libboost-iostreams1.42.0
  libboost-math1.42-dev libboost-math1.42.0 libboost-program-options1.42-dev
  libboost-program-options1.42.0 libboost-python1.42-dev libboost-python1.42.0
  libboost-regex1.42-dev libboost-regex1.42.0 libboost-serialization1.42-dev
  libboost-serialization1.42.0 libboost-signals1.42-dev libboost-signals1.42.0
  libboost-system1.42-dev libboost-system1.42.0 libboost-test1.42-dev
  libboost-test1.42.0 libboost-thread1.42-dev libboost-thread1.42.0
  libboost-wave1.42-dev libboost-wave1.42.0 libboost1.42-dev libdrm-dev
  libgl1-mesa-dev libglu1-mesa-dev libice-dev libicu-dev libopenscenegraph-dev
  libopenthreads-dev libpthread-stubs0 libpthread-stubs0-dev libsm-dev
  libx11-dev libxau-dev libxcb1-dev libxdmcp-dev libxext-dev libxt-dev
  mesa-common-dev python-dev python2.6-dev x11proto-core-dev
  x11proto-input-dev x11proto-kb-dev x11proto-xext-dev xtrans-dev
Suggested packages:
  graphviz libboost1.42-doc doxygen docbook-xsl default-jdk fop fltk1.1-doc
  fluid libjpeg62-dev libpng12-0-dev libxft-dev libxinerama-dev icu-doc
.........
0 upgraded, 63 newly installed, 0 to remove and 1 not upgraded.
Need to get 36.2MB of archives.
After this operation, 164MB of additional disk space will be used."

Anyway, thanks for helping out those of us who aren't into compiling and dependency investigation...  :)

Looks like it's working - Note that I did not get any "finished" indication - after the script ran, Terminal just blinked off.
You should even add a desktop start icon for us lazy folks too.

Not sure why it asks for so much... that's not in the script, it only needs:

libopenal1 libopenal-dev libalut0 libalut-dev libplib1 libplib-dev zlib1g zlib1g-dev libfltk1.1 libfltk1.1-dev libboost1.42-all-dev simgear-dev

Well, glad you got it working.  The script actually does say "Installation complete."  The reason you didn't see it was because you probably double clicked on it and chose run in terminal.  If so, the terminal just blinks off when the script is done.

I suppose I could make a GUI to do everything...

---

### Post by lkjoel on 2011-07-26
I made a new patch, finishing the cleanup and adding a desktop icon.
To apply, download the attachment, open up a Terminal window, go to the download directory and type in it:
```
tar -xf downloadinstallfgrun.tar
patch downloadinstallfgrun.sh downloadinstallfgrun.patch
rm -f downloadinstallfgrun.tar downloadinstallfgrun.patch
```

---

### Post by ubudog on 2011-07-26
Thanks lkjoel for all the patches!  :P

---

### Post by emarkay on 2011-07-26
Yes, works fantastically. Thanks!

So anyway, can I remove any files now that it installed, like any of the"libbboost"  or the "-dev"s?

---

### Post by ubudog on 2011-07-26
I think so, I might be mistaken.  I believe it's just for compiling the program.  (someone please correct me if I'm wrong)

---

### Post by lkjoel on 2011-07-26
> **emarkay said:**
> Yes, works fantastically. Thanks!

So anyway, can I remove any files now that it installed, like any of the"libbboost"  or the "-dev"s?
You can remove the -devs.

---

### Post by ubudog on 2011-07-26
> **lkjoel said:**
> You can remove the -devs.

Thanks.  :)

---

### Post by lkjoel on 2011-07-26
Yet another patch, which will remove unnecessary packages at the cleanup time.
To patch, download the attachment, open up a Terminal window, go to the download directory and type in it:
```
tar -xf downloadinstallfgrun2.tar
patch downloadinstallfgrun.sh downloadinstallfgrun2.patch
rm -f downloadinstallfgrun2.*
```

---

### Post by emarkay on 2011-07-29
lkjoel, I ran the 2 scriptsand it appears to have udun FGRUN - there's no "fgrun" to be found in my File System...

I will re-run the main script and this time I will confirm that FGRUN works before doing your 2 additional scripts.

Well, there now is an icon on the desktop, now, after I re-ran the main script. I will see if there are any unused files. Will also wait to see any comments before doing anything more.

---

### Post by bossdave on 2011-08-03
I need some help with the errors listed below.   Thanks

wizard_funcs.o: In function `Wizard::scenarii_cb()':
/home/djr/Games/fgrun-1.5.2/src/wizard_funcs.cxx:1418: undefined reference to `readProperties(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, SGPropertyNode*, int, bool)'
collect2: ld returned 1 exit status
make[2]: *** [fgrun] Error 1
make[2]: Leaving directory `/home/djr/Games/fgrun-1.5.2/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/djr/Games/fgrun-1.5.2/src'
make: *** [all-recursive] Error 1
Making install in src
make[1]: Entering directory `/home/djr/Games/fgrun-1.5.2/src'
make  install-am
make[2]: Entering directory `/home/djr/Games/fgrun-1.5.2/src'
g++ -DLOCALEDIR=\"/usr/local/share/locale\" -g -O2   -o fgrun  wizard.o wizard_funcs.o advanced.o advanced_funcs.o AirportBrowser.o AirportTable.o Fl_Table.o Fl_Table_Row.o Fl_OSG.o Fl_Heading_Dial.o main.o io.o fgfsrc.o logwin.o parkingloader.o settings.o util.o run_posix.o fgrun_pty.o -lsgmodel -lsgscreen -lsgprops -lsgxml -lsgdebug -lsgbvh -lsgmaterial -lsgmodel -lsgutil -lsgstructure -lsgprops -lsgtgdb -lsgmath -lsgmisc -lsgbvh -lsgio -lsgbucket -lsgmodel -lsgutil -lplibsg -lplibul -lplibnet -losgParticle -losgSim -losgViewer -losgGA -losgText -losgDB -losgUtil -losg -lOpenThreads -lfltk_gl -lpthread  -lfltk -lXft -lGL -lXmu -lXt -lSM -lICE -lXi -lXext -lX11  -lm -lz -lutil -losgFX
wizard_funcs.o: In function `Wizard::aircraft_update(char const*)':
/home/djr/Games/fgrun-1.5.2/src/wizard_funcs.cxx:970: undefined reference to `readProperties(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, SGPropertyNode*, int, bool)'
wizard_funcs.o: In function `loadModel(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, SGPath const&)':
/home/djr/Games/fgrun-1.5.2/src/wizard_funcs.cxx:437: undefined reference to `readProperties(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, SGPropertyNode*, int, bool)'
/home/djr/Games/fgrun-1.5.2/src/wizard_funcs.cxx:470: undefined reference to `sg_io_exception::sg_io_exception(char const*, sg_location const&, char const*)'
wizard_funcs.o: In function `Wizard::scenarii_cb()':
/home/djr/Games/fgrun-1.5.2/src/wizard_funcs.cxx:1418: undefined reference to `readProperties(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, SGPropertyNode*, int, bool)'
collect2: ld returned 1 exit status
make[2]: *** [fgrun] Error 1
make[2]: Leaving directory `/home/djr/Games/fgrun-1.5.2/src'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/djr/Games/fgrun-1.5.2/src'
make: *** [install-recursive] Error 1
Installation complete.  You should now be able to open fgrun by typing the following command into a terminal: fgrun

---

### Post by ubudog on 2011-08-04
Guys - 
I am in the process of rewriting the script to make the source code a bit simpler, and to include the fixes from lkjoel.

---

### Post by lkjoel on 2011-08-04
> **bossdave said:**
> I need some help with the errors listed below.   Thanks

wizard_funcs.o: In function `Wizard::scenarii_cb()':
/home/djr/Games/fgrun-1.5.2/src/wizard_funcs.cxx:1418: undefined reference to `readProperties(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, SGPropertyNode*, int, bool)'
collect2: ld returned 1 exit status
make[2]: *** [fgrun] Error 1
make[2]: Leaving directory `/home/djr/Games/fgrun-1.5.2/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/djr/Games/fgrun-1.5.2/src'
make: *** [all-recursive] Error 1
Making install in src
make[1]: Entering directory `/home/djr/Games/fgrun-1.5.2/src'
make  install-am
make[2]: Entering directory `/home/djr/Games/fgrun-1.5.2/src'
g++ -DLOCALEDIR=\"/usr/local/share/locale\" -g -O2   -o fgrun  wizard.o wizard_funcs.o advanced.o advanced_funcs.o AirportBrowser.o AirportTable.o Fl_Table.o Fl_Table_Row.o Fl_OSG.o Fl_Heading_Dial.o main.o io.o fgfsrc.o logwin.o parkingloader.o settings.o util.o run_posix.o fgrun_pty.o -lsgmodel -lsgscreen -lsgprops -lsgxml -lsgdebug -lsgbvh -lsgmaterial -lsgmodel -lsgutil -lsgstructure -lsgprops -lsgtgdb -lsgmath -lsgmisc -lsgbvh -lsgio -lsgbucket -lsgmodel -lsgutil -lplibsg -lplibul -lplibnet -losgParticle -losgSim -losgViewer -losgGA -losgText -losgDB -losgUtil -losg -lOpenThreads -lfltk_gl -lpthread  -lfltk -lXft -lGL -lXmu -lXt -lSM -lICE -lXi -lXext -lX11  -lm -lz -lutil -losgFX
wizard_funcs.o: In function `Wizard::aircraft_update(char const*)':
/home/djr/Games/fgrun-1.5.2/src/wizard_funcs.cxx:970: undefined reference to `readProperties(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, SGPropertyNode*, int, bool)'
wizard_funcs.o: In function `loadModel(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, SGPath const&)':
/home/djr/Games/fgrun-1.5.2/src/wizard_funcs.cxx:437: undefined reference to `readProperties(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, SGPropertyNode*, int, bool)'
/home/djr/Games/fgrun-1.5.2/src/wizard_funcs.cxx:470: undefined reference to `sg_io_exception::sg_io_exception(char const*, sg_location const&, char const*)'
wizard_funcs.o: In function `Wizard::scenarii_cb()':
/home/djr/Games/fgrun-1.5.2/src/wizard_funcs.cxx:1418: undefined reference to `readProperties(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, SGPropertyNode*, int, bool)'
collect2: ld returned 1 exit status
make[2]: *** [fgrun] Error 1
make[2]: Leaving directory `/home/djr/Games/fgrun-1.5.2/src'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/djr/Games/fgrun-1.5.2/src'
make: *** [install-recursive] Error 1
Installation complete.  You should now be able to open fgrun by typing the following command into a terminal: fgrun
That's a bug in FGRun. Try FGStartup: fgstartup.sourceforge.net

---

### Post by emarkay on 2011-08-09
Hey guys, I see there's a new player to those that gooey FG, FGStartup.  Looks like it's much smaller and is for those that don't need 3D representations of aircraft choices and TerraSync.

I did like FGRun, but I would like to try this new one. For us who are compiler-challenged, is it possible to make a script or get a .deb file of FGStartup for Lucid?

I had to reinstall FG anyway today, so... :) 

Thanks!

---

### Post by lkjoel on 2011-08-09
Sure, we'll make a script.

---

### Post by ubudog on 2011-08-09
> **emarkay said:**
> Hey guys, I see there's a new player to those that gooey FG, FGStartup.  Looks like it's much smaller and is for those that don't need 3D representations of aircraft choices and TerraSync.

I did like FGRun, but I would like to try this new one. For us who are compiler-challenged, is it possible to make a script or get a .deb file of FGStartup for Lucid?

I had to reinstall FG anyway today, so... :) 

Thanks!

Yep, lkjoel and I are the devs.  :-)

The easiest way to get the latest and greatest is to use svn:

```
svn co https://fgstartup.svn.sourceforge.net/svnroot/fgstartup fgstartup

```

Then, the latest build is located in FGStartup-build.  Enjoy!  :P

---

### Post by lkjoel on 2011-08-09
I added a build script.

---

### Post by emarkay on 2011-08-09
> **lkjoel said:**
> I added a build script.

Got it, have it installed and I get a program!

Unfortunately when I select a default plane (c-172) before I can start or preview, the program exits.

Do you want to debug this here or elsewhere? Willing to work with y'all on this!

Q, Why the sickly vibrant orange for the background of the airplane selection dialog area, and how does it know all those planes exist - many I am not familiar with - is it pulling the data from somewhere? 

I have a clean FGFS to play with, too.  Let me know.
MRK

---

### Post by lkjoel on 2011-08-09
I have the same problem. I'll see what I can do.

---

### Post by lkjoel on 2011-08-09
I fixed it.

---

### Post by emarkay on 2011-08-09
OK, now for the unenlightened, do I download all the files and run the script again or just replace one?

---

### Post by ubudog on 2011-08-09
> **emarkay said:**
> OK, now for the unenlightened, do I download all the files and run the script again or just replace one?
Try running the script again.  :-)

---

### Post by emarkay on 2011-08-11
I see there's a compiled version now (#44 I recall)  I kept getting an error last night when I ran it - can you test and ensure it's OK?    

I am sorry I didn't copy the error and for some reason I can't re-exe it now...

---

### Post by lkjoel on 2011-08-11
It's OK for me.
Try re-compiling it.

---

### Post by emarkay on 2011-08-24
Update - I stopped working on this when I saw FG 2.4 was nearby - now that that's out, any recent changes on this?

BTW, have you gotten a compiled 2.4 working in Linux?

---

### Post by ubudog on 2011-08-24
> **emarkay said:**
> Update - I stopped working on this when I saw FG 2.4 was nearby - now that that's out, any recent changes on this?

BTW, have you gotten a compiled 2.4 working in Linux?

Not yet, but I'm planning on installing 10.04 later on for testing, and I'll compile 2.4 on there, and compile Fgrun using the script, and make sure everything works.   I'll keep you posted.  ;-)

---

### Post by lkjoel on 2011-08-24
I've got 2.4 from Playdeb.net.

---

### Post by ubudog on 2011-08-24
> **lkjoel said:**
> I've got 2.4 from Playdeb.net.

Cool, but apparently it's only available for 11.04...

---

### Post by lkjoel on 2011-08-24
I guess you could "hack" the sources file to pretend that you are natty...
I don't know if that is a good idea though!

---

### Post by ubudog on 2011-08-25
> **lkjoel said:**
> I guess you could "hack" the sources file to pretend that you are natty...
I don't know if that is a good idea though!

Lol, I guess you could, but I've had many a problems doing that!  ;-)

---

### Post by pslat on 2011-09-10
Thanks Ubudog, I was nearly giving up on fgrun until I found this. I couldn't run fgrun since updating my system with package manager on 10.10, although I could run fgfs directly.
- I kept getting the error: fgrun: error while loading shared libraries: libosgParticle.so
Back in the cockpit again thanks to you.:D

---

### Post by ubudog on 2011-09-10
> **pslat said:**
> Thanks Ubudog, I was nearly giving up on fgrun until I found this. I couldn't run fgrun since updating my system with package manager on 10.10, although I could run fgfs directly.
- I kept getting the error: fgrun: error while loading shared libraries: libosgParticle.so
Back in the cockpit again thanks to you.:D

That's great!  Really glad it helped you.  

PS: Thanks to lkjoel also for all the patches!

---

