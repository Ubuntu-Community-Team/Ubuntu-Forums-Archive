---
title: "HPLIP won't install on 9.04"
date: 2009-04-05
forum: General Help
---

### Post by SilentSentinel on 2009-04-05
When running sh hplip-3.9.2.run on ubuntu 9.04 I get the error below after it has tried to install... any body else had a similar problem?


BUILD AND INSTALL
-----------------
Running './configure --with-drvdir=/usr/share/cups/drv/hp/ --with-hpppddir=/usr/share/ppd/hpijs/HP --prefix=/usr --enable-qt4 --enable-doc-build --disable-qt3 --disable-pp-build --enable-foomatic-drv-install --disable-foomatic-ppd-install --enable-network-build --enable-dbus-build --disable-hpijs-only-build --enable-scan-build --enable-fax-build'
Please wait, this may take several minutes...

error: Configure failed with error: python-devel not found

---

### Post by mousestalker on 2009-05-03
I had the same problem. I went to synaptic and installed every pythonx.x-dev app I could find. HPLIP installed after that.

There's something to be said about the 'brute force and sledgehammer' approach.

:)

---

### Post by fooman on 2009-05-03
just install the version from synaptic (system > administration > synaptic package manager....search for hplip)

it should be version 3.9.2 (jaunty) and should install any needed dependencies.

---

### Post by RealG187 on 2009-06-03
Does 9.04 come with HPLIP? I have an Office Jet (6300 I believe) and I wanna scan some stuff now!

EDIT: [http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)
I got it from there

---

### Post by colmhopkins on 2009-10-25
l think this might help.  Worked for me.
This is a solution for users getting the "python-devel not found error" when attempting installation of HPLIP.  It is also a guide for HP C4580 users to enable wireless printing and scanning.

Enjoy!!
sudo apt-get update

Pick appropriate command for your distro.

For Ubuntu 6.06 (Dapper) / 6.10 (Edgy) / 7.04 (Feisty) / 7.10 (Gutsy) / 8.04 (Hardy) / 8.10 (Intrepid) / 9.04 (Jaunty)
sudo aptitude install --assume-yes libcupsys2 cupsddk cupsddk-drivers libcupsys2-dev cupsys-bsd libcupsimage2-dev libdbus-1-dev build-essential gs-esp openssl libjpeg62-dev libsnmp-dev libtool libusb-dev python-imaging policykit policykit-gnome python-qt4 python-qt4-dbus python-dbus python-gobject python-dev python-notify python python-reportlab libsane libsane-dev sane-utils xsane

For Ubuntu 5.04 (Hoary) / 5.10 (Breezy)
sudo aptitude install --assume-yes libcupsys libcupsys2-dev cupsys-bsd libcupsys-dev build-essential gs-esp openssl libjpeg62-dev libsnmp5-dev libtool libusb-dev python-imaging python-qt4 python-qt4-dbus python-dev python python-reportlab sane libsane-dev sane-utils xsane

Download HPLIP from here 

[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

Go to the directory where you downloaded the HPLIP.
Example.

cd ~/Desktop

Then

sh hplip-3.9.8.run

Follow the prompts and HPLIP should be successfully installed.

For HP C4580 Users, at the point where HPLIP requires a restart/replug.  Press q for quit.

Enter the following 
sudo  gedit /usr/share/hplip/data/models/models.dat

Scroll down to [photosmart_c4500_series]

Change wifi-config=0 to wifi-config=1

Save and exit.

Next type

hp-setup

Follow the setup and enjoy wireless printing and scanning. 


:popcorn:Colm

---

### Post by fopetesl on 2010-01-24
Well. Didn't work for me :( :```
DISTRO/OS CONFIRMATION
----------------------
Distro appears to be Ubuntu 5.10.

Is "Ubuntu 5.10" your correct distro/OS and version (y=yes*, n=no, q=quit) ? y


ENTER ROOT/SUPERUSER PASSWORD
-----------------------------
Please enter the root/superuser password:
Password accepted


RUNNING PRE-INSTALL COMMANDS
----------------------------
OK


INSTALL MISSING OPTIONAL DEPENDENCIES
-------------------------------------
warning: There are 7 missing OPTIONAL dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency for option 'gui_qt4': pyqt4-dbus (PyQt 4 DBus - DBus Support for PyQt4)
warning: This installer cannot install 'pyqt4-dbus' for your distro/OS and/or version.
warning: Option 'gui_qt4' has been turned off.
warning: Missing REQUIRED dependency for option 'gui_qt4': pyqt4 (PyQt 4- Qt interface for Python (for Qt version 4.x))
warning: This installer cannot install 'pyqt4' for your distro/OS and/or version.
warning: Option 'gui_qt4' has been turned off.
warning: Missing OPTIONAL dependency for option 'gui_qt4': policykit (PolicyKit - Administrative policy framework)
warning: This installer cannot install 'policykit' for your distro/OS and/or version.
warning: Missing OPTIONAL dependency for option 'gui_qt4': python-notify (Python libnotify - Python bindings for the libnotify Desktop notifications)
warning: This installer cannot install 'python-notify' for your distro/OS and/or version.
warning: Missing REQUIRED dependency for option 'fax': python-dbus (Python DBus - Python bindings for DBus)
warning: This installer cannot install 'python-dbus' for your distro/OS and/or version.
warning: Option 'fax' has been turned off.
warning: Missing OPTIONAL dependency for option 'fax': reportlab (Reportlab - PDF library for Python)
warning: This installer cannot install 'reportlab' for your distro/OS and/or version.
warning: Missing REQUIRED dependency for option 'fax': dbus (DBus - Message bus system)
warning: This installer cannot install 'dbus' for your distro/OS and/or version.warning: Option 'fax' has been turned off.


PRE-BUILD COMMANDS
------------------
OK


BUILD AND INSTALL
-----------------
Running './configure --prefix=/usr --disable-qt4 --enable-doc-build --disable-cups-ppd-install --disable-foomatic-drv-install --enable-foomatic-ppd-install --enable-hpijs-install --disable-policykit --disable-cups-drv-install --disable-hpcups-install --enable-network-build --disable-dbus-build --enable-scan-build --disable-fax-build'
Please wait, this may take several minutes...
Command completed successfully.

Running 'make clean'
Please wait, this may take several minutes...
Command completed successfully.

Running 'make'
Please wait, this may take several minutes...
error: 'make' command failed with status code 2
~/My Downloads$
```
Any clues?
Dependencies missing?

---

### Post by metra on 2010-04-20
@ colmhopkins  thank you!

It didn't completely solve my problem, but at least with your instructions I saved a ton of time tracking down the dependency issues.

---

### Post by machine^R on 2010-05-03
To solve error 2 remove any spaces from the installation path as recommended here

[https://bugs.launchpad.net/hplip/+bug/490592](https://bugs.launchpad.net/hplip/+bug/490592)

---

### Post by Joshimitsu on 2010-12-13
Hi everyone.

I'm trying to install my HP Photosmart Perm C310 and have tried to install hplip.  I get the following error in terminal when I run sh hplip-3.10.9.run

error: 'make' command failed with status code 2

I've done a few searches online and a few suggest there's a space in the path name, but that's not the case with me.  There's no space in the path name.

Any ideas what I need to to?

Thanks

---

