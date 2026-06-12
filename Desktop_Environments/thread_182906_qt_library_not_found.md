---
title: "qt library not found?"
date: 2006-05-27
forum: Desktop Environments
---

### Post by linuxa on 2006-05-27
Hi there

I'm in the process of compiling & installing skim 1.4.4 from source code.

When running ./configure in the install directory. I get the following:

[B]Checking for Python               :  /usr/bin/python
Checking for SCons                :  Use Bundled scons.
Checking for kde-config           :  kde-config was found
Checking for kde version          :  3.4.3
Checking for the qt library       :  qt was not found
Please set QTDIR first (/usr/lib/qt3?) or try scons -h for more options[/B]

I currently have installed:
* libqt3-headers
* libqt3-mt
* libqt-mt-dev
* qt-dev-tools

After setting **QTDIR=/usr/lib/qt3** (is the qt library meant to be install there??), I still get the same error messages. 

And was wondering:
1) What package do I need for the qt libraries to be properly used in the configuration?
2) I suspect that I do have (1) covered (i.e. the libraries installed), but don't really know where at, how do I go about finding out where it went so that QTDIR could be properly set?

Thanks in advance for the help.

---

### Post by asimon on 2006-05-31
It seems you have everything installed and the build system of skim should find the Qt libraries on a Debian system automagically...

To see where a package installed it's files you can use 'dpkg -L <package>', for example
```

dpkg -L libqt3-mt-dev

```
The graphical package managers Apt or Synaptics should be able to show you the installed files too.

For QTDIR I would use /usr/share/qt3 as directory. /usr/lib/qt3 only contains plugins for Qt.

---

### Post by ktulu1115 on 2006-06-09
I'm having the same problem, trying to compile madman.  I did a dpkg -L on libqt3-mt-dev and got the following:

```
$ dpkg -L libqt3-mt-dev
/.
/usr
/usr/share
/usr/share/qt3
/usr/share/qt3/.qmake.cache
/usr/share/qt3/lib
/usr/share/doc
/usr/share/doc/libqt3-mt-dev
/usr/share/doc/libqt3-mt-dev/changelog.gz
/usr/share/doc/libqt3-mt-dev/README
/usr/share/doc/libqt3-mt-dev/PLATFORMS
/usr/share/doc/libqt3-mt-dev/copyright
/usr/share/doc/libqt3-mt-dev/README.Debian.gz
/usr/share/doc/libqt3-mt-dev/changelog.Debian.gz
/usr/include
/usr/include/qt3
/usr/include/qt3/qconfig.h
/usr/include/qt3/qmodules.h
/usr/include/qt3/qgl.h
/usr/include/qt3/qglcolormap.h
/usr/include/qt3/qwidgetfactory.h
/usr/lib
/usr/lib/libqt-mt.la
/usr/lib/libqt-mt.prl
/usr/lib/libqui.prl
/usr/lib/pkgconfig
/usr/lib/pkgconfig/qt-mt.pc
/usr/share/qt3/plugins
/usr/share/qt3/include
/usr/share/qt3/lib/libqt-mt.so
/usr/share/qt3/lib/libqt-mt.prl
/usr/share/qt3/lib/libqui.so
/usr/share/qt3/lib/libqui.prl
/usr/lib/libqt-mt.so
/usr/lib/libqui.so
```

Tried passing a number of these as qt_directory variables to scons, but no luck.

---

### Post by FrankVdb on 2006-12-03
I've got the same problem when trying to install the Polymer skin for Scribus...

---

### Post by -Phi- on 2006-12-07
I have a foggy suspicion that this thread might help: [http://www.ubuntuforums.org/showthread.php?t=76633](http://www.ubuntuforums.org/showthread.php?t=76633)

It worked for me.

- Phi

---

### Post by ktulu1115 on 2006-12-08
Well my problem ended up being something *stupid*, I didn't have g++ installed. :mad:

It may be a long shot, but it's possible you're missing a KDE library or something.

[http://ubuntuforums.org/showthread.php?t=147104&highlight=madman+qt](http://ubuntuforums.org/showthread.php?t=147104&highlight=madman+qt)

---

### Post by ktulu1115 on 2006-12-08
> **ktulu1115 said:**
> Well my problem ended up being something *stupid*, I didn't have g++ installed. :mad:

It may be a long shot, but it's possible you're missing a KDE library or something.

[http://ubuntuforums.org/showthread.php?t=147104&highlight=madman+qt](http://ubuntuforums.org/showthread.php?t=147104&highlight=madman+qt)

---

### Post by tdj2828 on 2008-01-10
Same problem here, but the following command line fixed this:

sudo apt-get install kdeutils-dev   

SKIM is looking for /usr/lib/libkdeui.la which doesn't exist until kdeutils-dev is
installed...though the libkdeui.so files might already exist anyway.

When in doubt...install the dev.  

Oh, and here is a great tip...how I found out it was looking for libkdeui.la...

strace sudo ./configure

strace is a powerful command...most of its output is senseless to me, but
a few lines (such as something along the lines of 'can't find /usr/lib/libkdeui.la')
are very useful in debugging recalcitrant issues.

---

