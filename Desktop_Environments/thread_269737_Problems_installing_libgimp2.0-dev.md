---
title: "Problems installing libgimp2.0-dev"
date: 2006-10-02
forum: Desktop Environments
---

### Post by leodp on 2006-10-02
Hi,
I'm trying to compile a module for gimp (on drapper drake), and for that I need gimptool; so I did:

apt-get install libgimp2.0-dev


Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgimp2.0-dev: Depends: libgtk2.0-dev (>= 2.4.4-1) but it is not going to be installed
E: Broken packages


So I went on:
apt-get   install libgtk2.0-dev
Getting:
The following packages have unmet dependencies:
  libgtk2.0-dev: Depends: libpango1.0-dev (>= 1.10.0-2) but it is not going to be installed
               Depends: libcairo2-dev but it is not going to be installed
E: Broken packages


and so on:
apt-get   install libpango1.0-dev
The following packages have unmet dependencies:
  libpango1.0-dev: Depends: libfreetype6-dev (>= 2.1.3) but it is not going to be installed
             Depends: libxft-dev but it is not going to be installed
             Depends: libfontconfig1-dev (>= 2.1.91) but it is not going to be installed
             Depends: libcairo2-dev (>= 1.0.0) but it is not going to be installed
E: Broken packages

and on:
apt-get   install libcairo2-dev
The following packages have unmet dependencies:
  libcairo2-dev: Depends: libcairo2 (= 1.0.4-0ubuntu1) but 1.2.2-0ubuntu2 is to be installed
         Depends: libfontconfig1-dev but it is not going to be installed
         Depends: libfreetype6-dev (>= 2.1.7) but it is not going to be installed
E: Broken packages


I must do something wrong, but I don't know how to move from here.
Any idea?

Thanks, Leo

---

### Post by pay on 2006-10-02
If you have the source package for gimp enabled in your /etc/apt/sources.list then you can simply ```
sudo apt-get build-dep gimp
```to download the packages required to compile. Also if you do ```
sudo apt-get --build source xxx
```where xxx is the package that you are trying to install it will download the source code and compile it for you. That may be helpful for installing packages for different distros.

---

### Post by leodp on 2006-10-02
Hi pay,
I don't get it compiled:

# sudo apt-get build-dep gimp
Reading package lists... Done
Building dependency tree... Done
E: Build-dependencies for gimp could not be satisfied.

# sudo apt-get --build source gimp
Reading package lists... Done
Building dependency tree... Done
Skipping already downloaded file 'gimp_2.2.11-1ubuntu3.1.dsc'
Skipping already downloaded file 'gimp_2.2.11.orig.tar.gz'
Skipping already downloaded file 'gimp_2.2.11-1ubuntu3.1.diff.gz'
Need to get 0B of source archives.
Skipping unpack of already unpacked source in gimp-2.2.11
dpkg-buildpackage: source package is gimp
dpkg-buildpackage: source version is 2.2.11-1ubuntu3.1
dpkg-buildpackage: source changed by Martin Pitt <martin.pitt@ubuntu.com>
dpkg-buildpackage: host architecture i386
dpkg-checkbuilddeps: Unmet build dependencies: intltool libxmu-dev | xlibs-dev libxpm-dev | xlibs-dev libxt-dev | xlibs-dev libaa1-dev libgtk2.0-dev (>= 2.4.4-1) libgtkhtml2-dev (>= 2.0.0) libjpeg62-dev libart-2.0-dev libpng-dev libtiff4-dev python-dev python-gtk2-dev libexif-dev (>= 0.6.12) libmng-dev librsvg2-dev (>= 2.7.2-2) libfontconfig1-dev (>= 2.2.0) libwmf-dev (>= 0.2.8-1.1) libfreetype6-dev
dpkg-buildpackage: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: (Use -d flag to override.)
Build command 'cd gimp-2.2.11 && dpkg-buildpackage -b -uc' failed.
E: Child process failed


And similar for the other packages:
# sudo apt-get --build source libgtk2.0-dev
Reading package lists... Done
Building dependency tree... 50%
Building dependency tree... Done
Skipping already downloaded file 'gtk+2.0_2.8.20-0ubuntu1.dsc'
Skipping already downloaded file 'gtk+2.0_2.8.20.orig.tar.gz'
Skipping already downloaded file 'gtk+2.0_2.8.20-0ubuntu1.diff.gz'
Need to get 0B of source archives.
Skipping unpack of already unpacked source in gtk+2.0-2.8.20
dpkg-buildpackage: source package is gtk+2.0
dpkg-buildpackage: source version is 2.8.20-0ubuntu1
dpkg-buildpackage: source changed by Sebastien Bacher <seb128@canonical.com>
dpkg-buildpackage: host architecture i386
dpkg-checkbuilddeps: Unmet build dependencies: libpango1.0-dev (>= 1.10.0-2) libatk1.0-dev (>= 1.9.0) libxrandr-dev libxt-dev libxrender-dev libxft-dev libxcursor-dev libxkbfile-dev libxinerama-dev libxfixes-dev libcairo2-dev libtiff4-dev libjpeg62-dev libpng12-dev docbook-utils linuxdoc-tools-text gnome-pkg-tools gtk-doc-tools
dpkg-buildpackage: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: (Use -d flag to override.)
Build command 'cd gtk+2.0-2.8.20 && dpkg-buildpackage -b -uc' failed.
E: Child process failed


My sources.list looks like:
# Ubuntu 'Main' Repository
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted

# Ubuntu 'Universe' Repository
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse

# Ubuntu 'Backports' Repository
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

# Ubuntu Bug Fix Updates
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted

# Ubuntu Security Updates
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# PLF - Collection of Non-Free Proprietary Codecs & Applications
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free

# WINE - Windows API for Linux
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

# REALPLAYER
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main


Ciao, Leo

---

### Post by pay on 2006-10-02
You can try to find the packages here [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by leodp on 2006-10-02
Gosh, I had to manually download/install (in I don't remember which order):


libexpat1-dev_1.95.8-3_i386.deb                
libfreetype6_2.1.10-1ubuntu2.2_i386.deb      
libxrender-dev_0.9.0.2-0ubuntu2_i386.deb
libfontconfig1_2.3.2-1.1ubuntu12_i386.deb      
libfreetype6-dev_2.1.10-1ubuntu2.2_i386.deb  
x-dev_7.0.4-0ubuntu2_all.deb
libfontconfig1-dev_2.3.2-1.1ubuntu12_i386.deb  
libxft-dev_2.1.8.2-0ubuntu2_i386.deb
libatk1.0-dev_1.11.4-0ubuntu1_i386.deb    
libpng12-dev_1.2.8rel-5_i386.deb          
libxrandr-dev_1.1.0.2-0ubuntu4_i386.deb
libcairo2_1.0.4-0ubuntu1_i386.deb      
libxcursor-dev_1.1.5.2-0ubuntu4_i386.deb  
x11proto-fixes-dev_3.0.2-0ubuntu2_all.deb
libcairo2-dev_1.0.4-0ubuntu1_i386.deb    
 libxfixes3_3.0.1.2-0ubuntu3_i386.deb      
x11proto-xinerama-dev_1.1.2-0ubuntu2_all.deb
libpango1.0-0_1.12.2-0ubuntu3_i386.deb    
libxfixes-dev_3.0.1.2-0ubuntu3_i386.deb
libpango1.0-dev_1.12.2-0ubuntu3_i386.deb  
libxinerama-dev_1.0.1-0ubuntu2_i386.deb
libgimp2.0-dev_2.2.11-1ubuntu3.1_i386.deb  
libgtk2.0-0_2.8.17-1ubuntu5_i386.deb  
libgtk2.0-dev_2.8.17-1ubuntu5_i386.deb

Maybe next time I'll check the sources before starting.
Thanks pay,
Ciao, Leo

---

