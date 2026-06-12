---
title: "CyMotion Master Linux keyboard"
date: 2006-06-21
forum: Desktop Environments
---

### Post by KimJarvis on 2006-06-21
I bought a CyMotion Master Linux keyboard.  The software installed in moments on windows and it is very convenient to use.  However installing this supposedly linux keyboard on Ubuntu is well beyond a casual open office user like myself.  Did anyone install this keyboard software on ubuntu 6.06 AMD64?

This is how far I got following the installation instructions:

1) In order to use all the keys the kernel must be patched and rebuilt!!!  The first step involves changing directory to a directory that does not exist in my installation.  

Change directory:
cd /usr/src/linux/drivers/usb/input/

2) The keyman application is used to set up the special keys.  The installation CD includes a debian package, but it is built for the i386.  In order to install on my AMD64 machine I have to rebuild the debian package.  The debian instructions  don't really describe what to do.

  * debian packages are build from a clean tree
  * become root (su or sudo or whatever you like)
    ./debian/rules binary
  * the result is a debian package in the folder above the source folder


The full installation files are included below:

Copyright (c) 2005 CHERRY GMBH

Readme

30/11/2005

******************************





Table of Contents

=================

1. User management

2. Patching the Linux-kernel

3. Version collisions

4. Known Bug list





1. User management

------------------

Users who are using the KeyMan-software must be a member of the 

group 'keyman'.

Adding the user test to the group keyman:

"usermod -A keyman test"





2. Patching the Linux-kernel

----------------------------

To use all additional keys of the Cherry-keyboard you have carry out an 

update of the kernel.



2.1 Run the kernel-patch

~~~~~~~~~~~~~~~~~~~~~~~~

Change directory:

cd /usr/src/linux/drivers/usb/input/



Rebuild hid-input.c:

patch hid-input.c ~USERNAME/keyman/kernel/hid-input.c.diff



Rebuild hid-core.c:

patch hid-core.c ~USERNAME/keyman/kernel/hid-core.c.diff



3.2 Compiling a new kernel

~~~~~~~~~~~~~~~~~~~~~~~~~~

Go as root to the source-directory of the kernel:

cd /usr/src/linux/



Call the configuration-tool for modules of the new kernel:

"make xconfig"



Modules which are absolutely necessary for starting the system, must be 

bounded to the kernel by assigning them with a check mark. Modules that 

are not required for booting can also be loaded later (mark those with 

a dot).

Note: all settings are depending upon the hardware of your system.



Important modules are: (in case of availability on the system)

- Filesystem (e. g. Ext3) support

- ATA/ATAPI support

- SCSI device support



After finishing the configuration save and close the tool.

Then run the commands in the following sequence:

1) make

2) make modules

3) make modules_install

4) make bzImage



Your new kernel is now ready and saved at: 

/usr/src/linux/arch/i386/boot/bzImage



If the bootloader "grub" is installed open /boot/grub/menu.lst with an 

editor (e.g. vi) and add a new starting-option:

"vi /boot/grub/menu.lst"



Create a copy of the entry from the old kernel with a different name and 

change the kernel-path to:

/usr/src/linux/arch/i368/boot/bzImage



Now you can perform a reboot. On starting up, the new kernel can be chosen.





3. KnownBug list

----------------

3.1 KeyMan-key doesn't work on PS/2

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

It's recommended to use the USB port on keyboards which can be connected 

via USB and PS/2. If you connect the keyboard on PS/2 the KeyMan-key 

doesn't work, so the function 'KeyMan + Additional Key' isn't available.



and... 


Table of Contents
=================

1.   Requirements
1.1  Software when using the daemon
1.2  Software needed to compile
1.3  How to build
1.4  Build Problems
2.   Installation
3.   Running
3.1  Systray program
3.2  Daemon
4.   Problems
4.1. "Daemon already running"
4.2. Crashes
4.3. USB
4.4. Some keys don't work for a user


1. Requirements
===============

1.1 Software when using the daemon
----------------------------------
* aumix
* eject
* evolution
* kcalc
* konqueror
* xmms
+ other software for which keyman is preconfigured for

1.2 Software needed to compile
------------------------------
* make
* gcc (the compiler collection)
* X11 development files
* QT (threaded version) + development files
* kde + development files
* libtool
* xerces + development files
* kernel header files (for inputdev plugin and input tunnel)
  (usually installed under /usr/include/linux)

1.3 How to build
------------------
Configure project
  ./configure
Build project
  make
Build binary archive package
  make package_bin
Build deb (Debian) package
  * debian packages are build from a clean tree
  * become root (su or sudo or whatever you like)
    ./debian/rules binary
  * the result is a debian package in the folder above the source folder
Build rpm (SuSE) package
  make package_rpm
Build source archive
  make package_src

All packages are built in the directory above the top level directory except
the rpm package which can be found in /usr/src/packages/RPMS/<arch> where
"<arch>" is something like "i586" (look at the output when building).


1.4 Build Problems
------------------
SuSE 9.1 ships a version of make that is not fully functional (GNU make version
3.80 has bugs which are known). In any case try an online update.
If you get "missing separator":
  Make tries to re-configure the package because some *.in files have
  changed. In that case just run "./configure" in the top-level directory.
If you get "memory exhausted":
   Download the latest cvs version.
      (It makes me wonder BTW why it did work on the other SuSE9.1 installation
       - maybe they fixed that problem by using the online update/patching
       system)
	In general this shouldn't happen as a workaround is integrated in the
   respective Makefiles.


2. Installation
===============
see INSTALL


3. Running
==========

3.1 Systray program
-------------------
Start systray program
   If you have installed the package a KDE-Menu Entry should have been created.
   Start the systray Application by selecting the "Keyman" entry.
   Otherwise run it manually by executing "kkeymansystray".
   The systray program takes care of starting the daemon automagically.


3.2 Server
----------
start server program
	a) with default (configurated) plugin
      * keymanserver
   b) with kde gui plugin
      * keymanserver --plugin /usr/share/keyman/plugins/kde-gui.so
   c) with console plugin
      * keymanserver --plugin /usr/share/cherry/plugins/console.so
To end the server
   press control+c (in case of the console plugin)
or type
	keymanserver --quit (console or kde-gui)


4. Problems
===========

4.1. "Server already running"
-----------------------------
If you see a message saying that the daemon is already running although the
daemon is actually not running, delete the file "/tmp/KeymanSocket_<UserName>".

4.2. Crashes
------------
If you installed the binary version and you get crashes, then this might be
due to differences in the installed packages on the build machine and your
machine. In this case try building from source.

4.3. USB
--------
If you want to use the additional keys of your CyMotion Linux keyboard with
USB, you have to recompile the kernel-module "hid".
For further instructions on how to recompile parts of your kernel, please see
documentation included in your distribution or visit [www.kernel.org](www.kernel.org)
Apply cymolin/kernel/drivers/usb/input/hid-input.c.diff to
/usr/src/linux/drivers/usb/input/hid-input.c before compiling.

Example:
cd /usr/src/linux/drivers/usb/input
patch hid-input.c < $HOME/cymolin/kernel/hid-input.c.diff

If you want to use a "normal" CyMotion Master Solar or a
CyMotion Master XPress, you also have to apply
cymolin/kernel/drivers/usb/input/hid-core.c.diff

And don't forget to copy your changed hid-module to the appropriate
location and do a "rmmod hid" and a "modprobe hid" or simply
reboot your system

4.4. Some keys don't work for a user
------------------------------------
* check wether the keys are configured correctly
* check wether the user is in the group "keyman"

---

