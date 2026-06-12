---
title: "Difference between install kde or install kde-desktop?"
date: 2005-07-18
forum: Desktop Environments
---

### Post by higgins on 2005-07-18
Hello there

I am new to Ubuntu and absolutly love it. I have been using Windows for years and now want to change to linux for good. I have tried Mandrake 10.1 and had various hardware problems. Ubuntu install and hardware configuration was seamless for me. Eveything worked and is working perfectly.

I would like to try out KDE. I have been searching the threads and want to know what is the difference between:

***sudo apt-get install kdm*** OR ***sudo apt-get install kdm-desktop?***

Which one should I use. I still want gnome but would like a choice.

 :)  :)

---

### Post by damonw5 on 2005-07-18
[QUOTE=higgins]Hello there

I am new to Ubuntu and absolutly love it. I have been using Windows for years and now want to change to linux for good. I have tried Mandrake 10.1 and had various hardware problems. Ubuntu install and hardware configuration was seamless for me. Eveything worked and is working perfectly.

I would like to try out KDE. I have been searching the threads and want to know what is the difference between:

***sudo apt-get install kdm*** OR ***sudo apt-get install kdm-desktop?***

Which one should I use. I still want gnome but would like a choice.

 :)  :)[/QUOTE]
 Hi higgins,

Glad to hear the good news about Ubuntu :)

KDM is a login manager that asks for your username and password in a graphical way, much like GDM (the default login manager).

KDE is a differrent desktop environment than GNOME. The best way to install KDE and a good selection of applications for it is to 

sudo apt-get install kubuntu-desktop

This is the best option unless you have limited Internet connectivity or limited hard drive space. I believe the install asks you if you want to install KDM or stay with GDM. Either one will allow you to boot either desktop environment.

Good luck and keep asking questions,

Damon

---

### Post by higgins on 2005-07-19
Hellow there, I have done: sudo apt-get install kdm-desktop,

However I get the following output.

```
ives/kdelibs-data_4%3a3.4.0-0ubuntu3.2_all.deb - open (2 No such file or directory)
E: Unable to determine the file size - fstat (9 Bad file descriptor)
E: Read error - read (9 Bad file descriptor)
E: Prior errors apply to /var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubuntu3.2_all.deb
Extracting templates from packages: 9%E: Could not open file /var/cache/apt/archives/akregator_4%3a3.4.0-0ubuntu10_i386.deb - open (2 No such file or directory)E: Unable to determine the file size - fstat (9 Bad file descriptor)
E: Read error - read (9 Bad file descriptor)
E: Prior errors apply to /var/cache/apt/archives/akregator_4%3a3.4.0-0ubuntu10_i386.deb
Extracting templates from packages: 10%E: Could not open file /var/cache/apt/archives/artsbuilder_4%3a3.4.0-0ubuntu3_i386.deb - open (2 No such file or directory)
E: Unable to determine the file size - fstat (9 Bad file descriptor)
E: Read error - read (9 Bad file descriptor)
E: Prior errors apply to /var/cache/apt/archives/artsbuilder_4%3a3.4.0-0ubuntu3_i386.deb
Extracting templates from packages: 11%E: Could not open file /var/cache/apt/archives/amarok-arts_2%3a1.2.3-1ubuntu4_i386.deb - open (2 No such file or directory)
E: Unable to determine the file size - fstat (9 Bad file descriptor)
E: Read error - read (9 Bad file descriptor)
E: Prior errors apply to /var/cache/apt/archives/amarok-arts_2%3a1.2.3-1ubuntu4_i386.deb
Extracting templates from packages: 11%E: Could not open file /var/cache/apt/archives/libsqlite3-0_3.0.8-3_i386.deb - open (2 No such file or directory)
E: Unable to determine the file size - fstat (9 Bad file descriptor)
E: Read error - read (9 Bad file descriptor)
E: Prior errors apply to /var/cache/apt/archives/libsqlite3-0_3.0.8-3_i386.deb
Extracting templates from packages: 12%E: Could not open file /var/cache/apt/archives/libtag1_1.3.1-1_i386.deb - open (2 No such file or directory)
E: Unable to determine the file size - fstat (9 Bad file descriptor)
E: Read error - read (9 Bad file descriptor)
E: Prior errors apply to /var/cache/apt/archives/libtag1_1.3.1-1_i386.deb
Extracting templates from packages: 12%E: Could not open file /var/cache/apt/archives/libtunepimp2_0.3.0-2ubuntu5_i386.deb - open (2 No such file or directory)
E: Unable to determine the file size - fstat (9 Bad file descriptor)
E: Read error - read (9 Bad file descriptor)
E: Prior errors apply to /var/cache/apt/archives/libtunepimp2_0.3.0-2ubuntu5_i386.deb
Extracting templates from packages: 13%E: Could not open file /var/cache/apt/archives/amarok_2%3a1.2.3-1ubuntu4_i386.deb - open (2 No such file or directory)
E: Unable to determine the file size - fstat (9 Bad file descriptor)
E: Read error - read (9 Bad file descriptor)
E: Prior errors apply to /var/cache/apt/archives/amarok_2%3a1.2.3-1ubuntu4_i386.deb
Extracting templates from packages: 14%E: Could not open file /var/cache/apt/archives/ark_4%3a3.4.0-0ubuntu2_i386.deb - open (2 No such file or directory)
E: Unable to determine the file size - fstat (9 Bad file descriptor)
E: Read error - read (9 Bad file descriptor)
E: Prior errors apply to /var/cache/apt/archives/ark_4%3a3.4.0-0ubuntu2_i386.debExtracting templates from packages: 14%E: Could not open file /var/cache/apt/archives/arts_1.4.0-0pre1ubuntu3_all.deb - open (2 No such file or directory)
E: Unable to determine the file size - fstat (9 Bad file descriptor)
E: Read error - read (9 Bad file descriptor)
E: Prior errors apply to /var/cache/apt/archives/arts_1.4.0-0pre1ubuntu3_all.debExtracting templates from packages: 16%E: Could not open file /var/cache/apt/archives/librss1_4%3a3.4.0-0ubuntu2.1_i386.deb - open (2 No such file or directory)E: Unable to determine the file size - fstat (9 Bad file descriptor)
E: Read error - read (9 Bad file descriptor)
E: Prior errors apply to /var/cache/apt/archives/librss1_4%3a3.4.0-0ubuntu2.1_i386.deb
Extracting templates from packages: 16%E: Could not open file /var/cache/apt/archives/dcoprss_4%3a3.4.0-0ubuntu2.1_i386.deb - open (2 No such file or directory)E: Unable to determine the file size - fstat (9 Bad file descriptor)
E: Read error - read (9 Bad file descriptor)
E: Prior errors apply to /var/cache/apt/archives/dcoprss_4%3a3.4.0-0ubuntu2.1_i386.deb
Extracting templates from packages: 19%E: Could not open file /var/cache/apt/archives/libkipi0_0.1-2_i386.deb - open (2 No such file or directory)
E: Unable to determine the file size - fstat (9 Bad file descriptor)
E: Read error - read (9 Bad file descriptor)
E: Prior errors apply to /var/cache/apt/archives/libkipi0_0.1-2_i386.deb
Extracting templates from packages: 19%E: Could not open file /var/cache/apt/archives/gwenview_1.2.0-0ubuntu2_i386.deb - open (2 No such file or directory)
E: Unable to determine the file size - fstat (9 Bad file descriptor)
E: Read error - read (9 Bad file descriptor)
E: Prior errors apply to /var/cache/apt/archives/gwenview_1.2.0-0ubuntu2_i386.deb
Extracting templates from packages: 20%E: Could not open file /var/cache/apt/archives/libtunepimp-bin_0.3.0-2ubuntu5_i386.deb - open (2 No such file or directory)
E: Unable to determine the file size - fstat (9 Bad file descriptor)
E: Read error - read (9 Bad file descriptor)
E: Prior errors apply to /var/cache/apt/archives/libtunepimp-bin_0.3.0-2ubuntu5_i386.deb
Extracting templates from packages: 21%E: Could not open file /var/cache/apt/archives/juk_4%3a3.4.0-0ubuntu3_i386.deb - open (2 No such file or directory)
E: Unable to determine the file size - fstat (9 Bad file descriptor)
E: Read error - read (9 Bad file descriptor)
E: Prior errors apply to /var/cache/apt/archives/juk_4%3a3.4.0-0ubuntu3_i386.debExtracting templates from packages: 22%E: Could not open file /var/cache/apt/archives/k3blibs_0.11.23-0ubuntu3_i386.deb - open (2 No such file or directory)
E: Unable to determine the file size - fstat (9 Bad file descriptor)
E: Read error - read (9 Bad file descriptor)
E: Prior errors apply to /var/cache/apt/archives/k3blibs_0.11.23-0ubuntu3_i386.deb
Extracting templates from packages: 23%E: Could not open file /var/cache/apt/archives/kdebase-bin_4%3a3.4.0-0ubuntu18_i386.deb - open (2 No such file or directory)
E: Unable to determine the file size - fstat (9 Bad file descriptor)
E: Read error - read (9 Bad file descriptor)
E: Prior errors apply to /var/cache/apt/archives/kdebase-bin_4%3a3.4.0-0ubuntu18_i386.deb
Extracting templates from packages: 100%d file descriptor
Preconfiguring packages ...
Selecting previously deselected package libqt3c102-mt.
(Reading database ... 60849 files and directories currently installed.)
Unpacking libqt3c102-mt (from .../libqt3c102-mt_3.3.3-7ubuntu3_i386.deb) ...
Selecting previously deselected package libarts1.
Unpacking libarts1 (from .../libarts1_1.4.0-0pre1ubuntu3_i386.deb) ...
Selecting previously deselected package libltdl3.
Unpacking libltdl3 (from .../libltdl3_1.5.6-5_i386.deb) ...
Selecting previously deselected package libsamplerate0.
Unpacking libsamplerate0 (from .../libsamplerate0_0.1.1-2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/akode_4%3a3.4.0-0ubuntu3_i386.deb (--unpack):
 cannot access archive: No such file or directory
Selecting previously deselected package libopenexr2.
Unpacking libopenexr2 (from .../libopenexr2_1.2.1-2_i386.deb) ...
Selecting previously deselected package libpcre3.
Unpacking libpcre3 (from .../libpcre3_4.5-1.1_i386.deb) ...
Selecting previously deselected package menu-xdg.
Unpacking menu-xdg (from .../menu-xdg_0.2ubuntu1_all.deb) ...
Selecting previously deselected package libnetpbm10.
Unpacking libnetpbm10 (from .../libnetpbm10_10.0-8_i386.deb) ...
Selecting previously deselected package netpbm.
Unpacking netpbm (from .../netpbm_10.0-8_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/kdelibs-bin_4%3a3.4.0-0ubuntu3.2_i386.deb (--unpack):
 cannot access archive: No such file or directory
dpkg: error processing /var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubuntu3.2_all.deb (--unpack):
 cannot access archive: No such file or directory
Selecting previously deselected package kdelibs4.
Unpacking kdelibs4 (from .../kdelibs4_4%3a3.4.0-0ubuntu3.2_i386.deb) ...
Selecting previously deselected package libktnef1.
Unpacking libktnef1 (from .../libktnef1_3.4.0-0ubuntu10_i386.deb) ...
Selecting previously deselected package libkdepim1.
Unpacking libkdepim1 (from .../libkdepim1_3.4.0-0ubuntu10_i386.deb) ...
Selecting previously deselected package libkcal2a.
Unpacking libkcal2a (from .../libkcal2a_3.4.0-0ubuntu10_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/akregator_4%3a3.4.0-0ubuntu10_i386.deb (--unpack):
 cannot access archive: No such file or directory
dpkg: error processing /var/cache/apt/archives/artsbuilder_4%3a3.4.0-0ubuntu3_i386.deb (--unpack):
 cannot access archive: No such file or directory
dpkg: error processing /var/cache/apt/archives/amarok-arts_2%3a1.2.3-1ubuntu4_i386.deb (--unpack):
 cannot access archive: No such file or directory
dpkg: error processing /var/cache/apt/archives/libsqlite3-0_3.0.8-3_i386.deb (--unpack):
 cannot access archive: No such file or directory
dpkg: error processing /var/cache/apt/archives/libtag1_1.3.1-1_i386.deb (--unpack):
 cannot access archive: No such file or directory
dpkg: error processing /var/cache/apt/archives/libtunepimp2_0.3.0-2ubuntu5_i386.deb (--unpack):
 cannot access archive: No such file or directory
dpkg: error processing /var/cache/apt/archives/amarok_2%3a1.2.3-1ubuntu4_i386.deb (--unpack):
 cannot access archive: No such file or directory
dpkg: error processing /var/cache/apt/archives/ark_4%3a3.4.0-0ubuntu2_i386.deb (--unpack):
 cannot access archive: No such file or directory
dpkg: error processing /var/cache/apt/archives/arts_1.4.0-0pre1ubuntu3_all.deb (--unpack):
 cannot access archive: No such file or directory
Selecting previously deselected package dbus-qt-1.
Unpacking dbus-qt-1 (from .../dbus-qt-1_0.23.4-0ubuntu3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/librss1_4%3a3.4.0-0ubuntu2.1_i386.deb (--unpack):
 cannot access archive: No such file or directory
dpkg: error processing /var/cache/apt/archives/dcoprss_4%3a3.4.0-0ubuntu2.1_i386.deb (--unpack):
 cannot access archive: No such file or directory
Selecting previously deselected package enscript.
Unpacking enscript (from .../enscript_1.6.4-6_i386.deb) ...
Selecting previously deselected package libpth2.
Unpacking libpth2 (from .../p/pth/libpth2_2.0.1-2_i386.deb) ...
Selecting previously deselected package gnupg-agent.
Unpacking gnupg-agent (from .../gnupg-agent_1.9.15-3ubuntu5_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libkipi0_0.1-2_i386.deb (--unpack):
 cannot access archive: No such file or directory
dpkg: error processing /var/cache/apt/archives/gwenview_1.2.0-0ubuntu2_i386.deb (--unpack):
 cannot access archive: No such file or directory
Selecting previously deselected package imagemagick.
Unpacking imagemagick (from .../imagemagick_6%3a6.0.6.2-2.1ubuntu1.1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libtunepimp-bin_0.3.0-2ubuntu5_i386.deb (--unpack):
 cannot access archive: No such file or directory
dpkg: error processing /var/cache/apt/archives/juk_4%3a3.4.0-0ubuntu3_i386.deb (--unpack):
 cannot access archive: No such file or directory
Selecting previously deselected package libflac++4.
Unpacking libflac++4 (from .../libflac++4_1.1.1-4_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/k3blibs_0.11.23-0ubuntu3_i386.deb (--unpack):
 cannot access archive: No such file or directory
dpkg: error processing /var/cache/apt/archives/kdebase-bin_4%3a3.4.0-0ubuntu18_i386.deb (--unpack):
 cannot access archive: No such file or directory
Selecting previously deselected package kdebase-data.
Unpacking kdebase-data (from .../kdebase-data_4%3a3.4.0-0ubuntu18_all.deb) ...
Selecting previously deselected package kcontrol.
Unpacking kcontrol (from .../kcontrol_4%3a3.4.0-0ubuntu18_i386.deb) ...
Selecting previously deselected package k3b.
Unpacking k3b (from .../k3b_0.11.23-0ubuntu3_i386.deb) ...
Selecting previously deselected package libgpgme11.
Unpacking libgpgme11 (from .../libgpgme11_1.0.1-2_i386.deb) ...
Selecting previously deselected package libkleopatra0a.
Unpacking libkleopatra0a (from .../libkleopatra0a_3.4.0-0ubuntu10_i386.deb) ...
Selecting previously deselected package kaddressbook.
Unpacking kaddressbook (from .../kaddressbook_3.4.0-0ubuntu10_i386.deb) ...
Selecting previously deselected package libmodplug0.
Unpacking libmodplug0 (from .../libmodplug0_0.7-3_i386.deb) ...
Selecting previously deselected package libxine1.
Unpacking libxine1 (from .../libxine1_1.0-1ubuntu3.2_i386.deb) ...
Selecting previously deselected package kaffeine.
Unpacking kaffeine (from .../kaffeine_0.6-0ubuntu2_i386.deb) ...
Selecting previously deselected package libkpimidentities1.
Unpacking libkpimidentities1 (from .../libkpimidentities1_3.4.0-0ubuntu10_i386.deb) ...
Selecting previously deselected package libmimelib1a.
Unpacking libmimelib1a (from .../libmimelib1a_3.4.0-0ubuntu10_i386.deb) ...
Selecting previously deselected package kalarm.
Unpacking kalarm (from .../kalarm_3.4.0-0ubuntu10_i386.deb) ...
Selecting previously deselected package kamera.
Unpacking kamera (from .../kamera_4%3a3.4.0-0ubuntu3_i386.deb) ...
Selecting previously deselected package kappfinder.
Unpacking kappfinder (from .../kappfinder_4%3a3.4.0-0ubuntu18_i386.deb) ...
Selecting previously deselected package karm.
Unpacking karm (from .../karm_4%3a3.4.0-0ubuntu10_i386.deb) ...
Selecting previously deselected package kate.
Unpacking kate (from .../kate_4%3a3.4.0-0ubuntu18_i386.deb) ...
Selecting previously deselected package libkcddb1.
Unpacking libkcddb1 (from .../libkcddb1_4%3a3.4.0-0ubuntu3_i386.deb) ...
Selecting previously deselected package kdemultimedia-kio-plugins.
Unpacking kdemultimedia-kio-plugins (from .../kdemultimedia-kio-plugins_4%3a3.4.0-0ubuntu3_i386.deb) ...
Selecting previously deselected package kaudiocreator.
Unpacking kaudiocreator (from .../kaudiocreator_4%3a3.4.0-0ubuntu3_i386.deb) ...Selecting previously deselected package kcalc.
Unpacking kcalc (from .../kcalc_4%3a3.4.0-0ubuntu2_i386.deb) ...
Selecting previously deselected package kcharselect.
Unpacking kcharselect (from .../kcharselect_4%3a3.4.0-0ubuntu2_i386.deb) ...
Selecting previously deselected package kcron.
Unpacking kcron (from .../kcron_4%3a3.4.0-0ubuntu1_i386.deb) ...
Selecting previously deselected package kde-style-lipstik.
Unpacking kde-style-lipstik (from .../kde-style-lipstik_1.0-2ubuntu4_i386.deb) ...
Selecting previously deselected package kdeadmin-kfile-plugins.
Unpacking kdeadmin-kfile-plugins (from .../kdeadmin-kfile-plugins_4%3a3.4.0-0ubuntu1_i386.deb) ...
Selecting previously deselected package kuser.
Unpacking kuser (from .../kuser_4%3a3.4.0-0ubuntu1_i386.deb) ...
Selecting previously deselected package secpolicy.
Unpacking secpolicy (from .../secpolicy_4%3a3.4.0-0ubuntu1_i386.deb) ...
Selecting previously deselected package kdeadmin.
Unpacking kdeadmin (from .../kdeadmin_4%3a3.4.0-0ubuntu1_all.deb) ...
Selecting previously deselected package kdebase-kio-plugins.
Unpacking kdebase-kio-plugins (from .../kdebase-kio-plugins_3.4.0-0ubuntu18_i386.deb) ...
Selecting previously deselected package libkonq4.
Unpacking libkonq4 (from .../libkonq4_4%3a3.4.0-0ubuntu18_i386.deb) ...
Selecting previously deselected package kdepasswd.
Unpacking kdepasswd (from .../kdepasswd_4%3a3.4.0-0ubuntu18_i386.deb) ...
Selecting previously deselected package poster.
Unpacking poster (from .../poster_20020830-2_i386.deb) ...
Selecting previously deselected package psutils.
Unpacking psutils (from .../psutils_1.17-17_i386.deb) ...
Selecting previously deselected package kdeprint.
Unpacking kdeprint (from .../kdeprint_4%3a3.4.0-0ubuntu18_i386.deb) ...
Selecting previously deselected package kdesktop.
Unpacking kdesktop (from .../kdesktop_4%3a3.4.0-0ubuntu18_i386.deb) ...
Selecting previously deselected package kfind.
Unpacking kfind (from .../kfind_4%3a3.4.0-0ubuntu18_i386.deb) ...
Selecting previously deselected package khelpcenter.
Unpacking khelpcenter (from .../khelpcenter_4%3a3.4.0-0ubuntu18_i386.deb) ...
Selecting previously deselected package kicker.
Unpacking kicker (from .../kicker_4%3a3.4.0-0ubuntu18_i386.deb) ...
Selecting previously deselected package klipper.
Unpacking klipper (from .../klipper_4%3a3.4.0-0ubuntu18_i386.deb) ...
Selecting previously deselected package kmenuedit.
Unpacking kmenuedit (from .../kmenuedit_4%3a3.4.0-0ubuntu18_i386.deb) ...
Selecting previously deselected package konqueror-nsplugins.
Unpacking konqueror-nsplugins (from .../konqueror-nsplugins_4%3a3.4.0-0ubuntu18_i386.deb) ...
Selecting previously deselected package konqueror.
Unpacking konqueror (from .../konqueror_4%3a3.4.0-0ubuntu18_i386.deb) ...
Selecting previously deselected package konsole.
Unpacking konsole (from .../konsole_4%3a3.4.0-0ubuntu18_i386.deb) ...
Selecting previously deselected package kpager.
Unpacking kpager (from .../kpager_4%3a3.4.0-0ubuntu18_i386.deb) ...
Selecting previously deselected package kpersonalizer.
Unpacking kpersonalizer (from .../kpersonalizer_4%3a3.4.0-0ubuntu18_i386.deb) ...
Selecting previously deselected package ksmserver.
Unpacking ksmserver (from .../ksmserver_4%3a3.4.0-0ubuntu18_i386.deb) ...
Selecting previously deselected package ksplash.
Unpacking ksplash (from .../ksplash_4%3a3.4.0-0ubuntu18_i386.deb) ...
Selecting previously deselected package libsensors3.
Unpacking libsensors3 (from .../libsensors3_2.8.8-7ubuntu2_i386.deb) ...
Selecting previously deselected package ksysguardd.
Unpacking ksysguardd (from .../ksysguardd_4%3a3.4.0-0ubuntu18_i386.deb) ...
Selecting previously deselected package ksysguard.
Unpacking ksysguard (from .../ksysguard_4%3a3.4.0-0ubuntu18_i386.deb) ...
Selecting previously deselected package libxcomposite1.
Unpacking libxcomposite1 (from .../libxcomposite1_6.8.2-10_i386.deb) ...
Selecting previously deselected package kwin.
Unpacking kwin (from .../kwin_4%3a3.4.0-0ubuntu18_i386.deb) ...
Selecting previously deselected package kdebase.
Unpacking kdebase (from .../kdebase_4%3a3.4.0-0ubuntu18_all.deb) ...
Selecting previously deselected package kdegraphics-kfile-plugins.
Unpacking kdegraphics-kfile-plugins (from .../kdegraphics-kfile-plugins_4%3a3.4.0-0ubuntu3_i386.deb) ...
Selecting previously deselected package kgamma.
Unpacking kgamma (from .../kgamma_4%3a3.4.0-0ubuntu3_i386.deb) ...
Selecting previously deselected package kghostview.
Unpacking kghostview (from .../kghostview_4%3a3.4.0-0ubuntu3_i386.deb) ...
Selecting previously deselected package kmrml.
Unpacking kmrml (from .../kmrml_4%3a3.4.0-0ubuntu3_i386.deb) ...
Selecting previously deselected package kolourpaint.
Unpacking kolourpaint (from .../kolourpaint_4%3a3.4.0-0ubuntu3_i386.deb) ...
Selecting previously deselected package libkscan1.
Unpacking libkscan1 (from .../libkscan1_4%3a3.4.0-0ubuntu3_i386.deb) ...
Selecting previously deselected package kooka.
Unpacking kooka (from .../kooka_4%3a3.4.0-0ubuntu3_i386.deb) ...
Selecting previously deselected package kpdf.
Unpacking kpdf (from .../kpdf_4%3a3.4.0-0ubuntu3_i386.deb) ...
Selecting previously deselected package ksnapshot.
Unpacking ksnapshot (from .../ksnapshot_4%3a3.4.0-0ubuntu3_i386.deb) ...
Selecting previously deselected package ksvg.
Unpacking ksvg (from .../ksvg_4%3a3.4.0-0ubuntu3_i386.deb) ...
Selecting previously deselected package kdegraphics.
Unpacking kdegraphics (from .../kdegraphics_4%3a3.4.0-0ubuntu3_all.deb) ...
Selecting previously deselected package kdemultimedia-kappfinder-data.
Unpacking kdemultimedia-kappfinder-data (from .../kdemultimedia-kappfinder-data_4%3a3.4.0-0ubuntu3_i386.deb) ...
Selecting previously deselected package kdemultimedia-kfile-plugins.
Unpacking kdemultimedia-kfile-plugins (from .../kdemultimedia-kfile-plugins_4%3a3.4.0-0ubuntu3_i386.deb) ...
Selecting previously deselected package kmix.
Unpacking kmix (from .../kmix_4%3a3.4.0-0ubuntu3_i386.deb) ...
Selecting previously deselected package kscd.
Unpacking kscd (from .../kscd_4%3a3.4.0-0ubuntu3_i386.deb) ...
Selecting previously deselected package libarts1-audiofile.
Unpacking libarts1-audiofile (from .../libarts1-audiofile_4%3a3.4.0-0ubuntu3_i386.deb) ...
Selecting previously deselected package libarts1-xine.
Unpacking libarts1-xine (from .../libarts1-xine_4%3a3.4.0-0ubuntu3_i386.deb) ...Selecting previously deselected package kdemultimedia.
Unpacking kdemultimedia (from .../kdemultimedia_4%3a3.4.0-0ubuntu3_all.deb) ...
Selecting previously deselected package kdenetwork-filesharing.
Unpacking kdenetwork-filesharing (from .../kdenetwork-filesharing_4%3a3.4.0-0ubuntu2.1_i386.deb) ...
Selecting previously deselected package knewsticker.
Unpacking knewsticker (from .../knewsticker_4%3a3.4.0-0ubuntu2.1_i386.deb) ...
Selecting previously deselected package libgadu3.
Unpacking libgadu3 (from .../libgadu3_1%3a1.5-4ubuntu1_i386.deb) ...
Selecting previously deselected package kopete.
Unpacking kopete (from .../kopete_4%3a3.4.0-0ubuntu2.1_i386.deb) ...
Selecting previously deselected package kpf.
Unpacking kpf (from .../kpf_4%3a3.4.0-0ubuntu2.1_i386.deb) ...
Selecting previously deselected package kppp.
Unpacking kppp (from .../kppp_4%3a3.4.0-0ubuntu2.1_i386.deb) ...
Selecting previously deselected package krdc.
Unpacking krdc (from .../krdc_4%3a3.4.0-0ubuntu2.1_i386.deb) ...
Selecting previously deselected package krfb.
Unpacking krfb (from .../krfb_4%3a3.4.0-0ubuntu2.1_i386.deb) ...
Selecting previously deselected package kwifimanager.
Unpacking kwifimanager (from .../kwifimanager_4%3a3.4.0-0ubuntu2.1_i386.deb) ...Selecting previously deselected package kdenetwork-kfile-plugins.
Unpacking kdenetwork-kfile-plugins (from .../kdenetwork-kfile-plugins_4%3a3.4.0-0ubuntu2.1_i386.deb) ...
Selecting previously deselected package kdenetwork.
Unpacking kdenetwork (from .../kdenetwork_4%3a3.4.0-0ubuntu2.1_all.deb) ...
Selecting previously deselected package kdepim-kfile-plugins.
Unpacking kdepim-kfile-plugins (from .../kdepim-kfile-plugins_4%3a3.4.0-0ubuntu10_i386.deb) ...
Selecting previously deselected package kdepim-kio-plugins.
Unpacking kdepim-kio-plugins (from .../kdepim-kio-plugins_3.4.0-0ubuntu10_i386.deb) ...
Selecting previously deselected package knotes.
Unpacking knotes (from .../knotes_3.4.0-0ubuntu10_i386.deb) ...
Selecting previously deselected package kdepim-wizards.
Unpacking kdepim-wizards (from .../kdepim-wizards_3.4.0-0ubuntu10_i386.deb) ...
Selecting previously deselected package kitchensync.
Unpacking kitchensync (from .../kitchensync_4%3a3.4.0-0ubuntu10_i386.deb) ...
Selecting previously deselected package libksieve0.
Unpacking libksieve0 (from .../libksieve0_3.4.0-0ubuntu10_i386.deb) ...
Selecting previously deselected package pinentry-qt.
Unpacking pinentry-qt (from .../pinentry-qt_0.7.1-5_i386.deb) ...
Selecting previously deselected package kmail.
Unpacking kmail (from .../kmail_3.4.0-0ubuntu10_i386.deb) ...
Selecting previously deselected package kmailcvt.
Unpacking kmailcvt (from .../kmailcvt_4%3a3.4.0-0ubuntu10_i386.deb) ...
Selecting previously deselected package knode.
Unpacking knode (from .../knode_4%3a3.4.0-0ubuntu10_i386.deb) ...
Selecting previously deselected package konsolekalendar.
Unpacking konsolekalendar (from .../konsolekalendar_4%3a3.4.0-0ubuntu10_i386.deb) ...
Selecting previously deselected package kontact.
Unpacking kontact (from .../kontact_3.4.0-0ubuntu10_i386.deb) ...
Selecting previously deselected package libkpimexchange1.
Unpacking libkpimexchange1 (from .../libkpimexchange1_3.4.0-0ubuntu10_i386.deb) ...
Selecting previously deselected package korganizer.
Unpacking korganizer (from .../korganizer_3.4.0-0ubuntu10_i386.deb) ...
Selecting previously deselected package libmal1.
Unpacking libmal1 (from .../libmal/libmal1_0.40-3_i386.deb) ...
Selecting previously deselected package kpilot.
Unpacking kpilot (from .../kpilot_3.4.0-0ubuntu10_i386.deb) ...
Selecting previously deselected package ksync.
Unpacking ksync (from .../ksync_3.4.0-0ubuntu10_i386.deb) ...
Selecting previously deselected package ktnef.
Unpacking ktnef (from .../ktnef_4%3a3.4.0-0ubuntu10_i386.deb) ...
Selecting previously deselected package networkstatus.
Unpacking networkstatus (from .../networkstatus_4%3a3.4.0-0ubuntu10_i386.deb) ...
Selecting previously deselected package libkgantt0.
Unpacking libkgantt0 (from .../libkgantt0_4%3a3.4.0-0ubuntu10_i386.deb) ...
Selecting previously deselected package kdepim.
Unpacking kdepim (from .../kdepim_4%3a3.4.0-0ubuntu10_all.deb) ...
Selecting previously deselected package kfloppy.
Unpacking kfloppy (from .../kfloppy_4%3a3.4.0-0ubuntu2_i386.deb) ...
Selecting previously deselected package kgpg.
Unpacking kgpg (from .../kgpg_4%3a3.4.0-0ubuntu2_i386.deb) ...
Selecting previously deselected package klaptopdaemon.
Unpacking klaptopdaemon (from .../klaptopdaemon_4%3a3.4.0-0ubuntu2_i386.deb) ...Selecting previously deselected package kmilo.
Unpacking kmilo (from .../kmilo_4%3a3.4.0-0ubuntu2_i386.deb) ...
Selecting previously deselected package kregexpeditor.
Unpacking kregexpeditor (from .../kregexpeditor_4%3a3.4.0-0ubuntu2_i386.deb) ...Selecting previously deselected package libsnmp-base.
Unpacking libsnmp-base (from .../libsnmp-base_5.1.2-6ubuntu2_all.deb) ...
Selecting previously deselected package libsnmp5.
Unpacking libsnmp5 (from .../libsnmp5_5.1.2-6ubuntu2_i386.deb) ...
Selecting previously deselected package ksim.
Unpacking ksim (from .../ksim_4%3a3.4.0-0ubuntu2_i386.deb) ...
Selecting previously deselected package kwalletmanager.
Unpacking kwalletmanager (from .../kwalletmanager_4%3a3.4.0-0ubuntu2_i386.deb) ...
Selecting previously deselected package kdeutils.
Unpacking kdeutils (from .../kdeutils_4%3a3.4.0-0ubuntu2_all.deb) ...
Selecting previously deselected package kubuntu-default-settings.
Unpacking kubuntu-default-settings (from .../kubuntu-default-settings_1%3a5.04-11_all.deb) ...
Selecting previously deselected package kdm.
Unpacking kdm (from .../kdm_4%3a3.4.0-0ubuntu18_i386.deb) ...
Selecting previously deselected package knetworkconf.
Unpacking knetworkconf (from .../knetworkconf_0.6.1-3ubuntu4_i386.deb) ...
Selecting previously deselected package libjpeg-progs.
Unpacking libjpeg-progs (from .../libjpeg-progs_6b-9_i386.deb) ...
Selecting previously deselected package konq-plugins.
Unpacking konq-plugins (from .../konq-plugins_4%3a3.4.0-0ubuntu2_i386.deb) ...
Selecting previously deselected package konserve.
Unpacking konserve (from .../konserve_0.10.3-1ubuntu1_i386.deb) ...
Selecting previously deselected package konversation.
Unpacking konversation (from .../konversation_0.18-1ubuntu1~5.04ubp2_i386.deb) ...
Selecting previously deselected package kscreensaver.
Unpacking kscreensaver (from .../kscreensaver_4%3a3.4.0-0ubuntu1_i386.deb) ...
Selecting previously deselected package kynaptic.
Unpacking kynaptic (from .../kynaptic_1%3a0.55+cvs20050115-0ubuntu6_i386.deb) ...
Selecting previously deselected package openoffice.org-kde.
Unpacking openoffice.org-kde (from .../openoffice.org-kde_1.1.3-8ubuntu2.3_i386.deb) ...
Selecting previously deselected package kubuntu-desktop.
Unpacking kubuntu-desktop (from .../kubuntu-desktop_0.40_i386.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/akode_4%3a3.4.0-0ubuntu3_i386.deb
 /var/cache/apt/archives/kdelibs-bin_4%3a3.4.0-0ubuntu3.2_i386.deb
 /var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubuntu3.2_all.deb
 /var/cache/apt/archives/akregator_4%3a3.4.0-0ubuntu10_i386.deb
 /var/cache/apt/archives/artsbuilder_4%3a3.4.0-0ubuntu3_i386.deb
 /var/cache/apt/archives/amarok-arts_2%3a1.2.3-1ubuntu4_i386.deb
 /var/cache/apt/archives/libsqlite3-0_3.0.8-3_i386.deb
 /var/cache/apt/archives/libtag1_1.3.1-1_i386.deb
 /var/cache/apt/archives/libtunepimp2_0.3.0-2ubuntu5_i386.deb
 /var/cache/apt/archives/amarok_2%3a1.2.3-1ubuntu4_i386.deb
 /var/cache/apt/archives/ark_4%3a3.4.0-0ubuntu2_i386.deb
 /var/cache/apt/archives/arts_1.4.0-0pre1ubuntu3_all.deb
 /var/cache/apt/archives/librss1_4%3a3.4.0-0ubuntu2.1_i386.deb
 /var/cache/apt/archives/dcoprss_4%3a3.4.0-0ubuntu2.1_i386.deb
 /var/cache/apt/archives/libkipi0_0.1-2_i386.deb
 /var/cache/apt/archives/gwenview_1.2.0-0ubuntu2_i386.deb
 /var/cache/apt/archives/libtunepimp-bin_0.3.0-2ubuntu5_i386.deb
 /var/cache/apt/archives/juk_4%3a3.4.0-0ubuntu3_i386.deb
 /var/cache/apt/archives/k3blibs_0.11.23-0ubuntu3_i386.deb
 /var/cache/apt/archives/kdebase-bin_4%3a3.4.0-0ubuntu18_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/home/tim #

```

When I try to log in via KDE I get could not start kdeinit error and KDE does not start.

Are there repositories I am suppposed to add before I start sudo apt-get install kdm-desktop? If so what are they?

---

### Post by higgins on 2005-07-20
Its all working correctly now

I did an update to kde-desktop via synaptic. Ubuntu really is great.

 :-|  :smile:  :smile:

---

