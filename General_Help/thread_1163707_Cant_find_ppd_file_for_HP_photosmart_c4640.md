---
title: "Cant find ppd file for HP photosmart c4640"
date: 2009-05-19
forum: General Help
---

### Post by Entity` on 2009-05-19
I just got a new HP photosmart c4640 all in one printer, but I can't find any ppd file for it anywhere.  I read that it is possible to extract a file from the drivers, but the guide I looked up was unclear as to how to do such a thing.

I know that HP printers have good support under linux, but is this one simply so new that no ppd file is out yet?

Thanks.

---

### Post by ewr2san on 2009-06-09
Also trying to get a new HP C4640 to work under ubuntu 9.04. Hplip did not find it with the default hplip that ships currently with Jaunty.

[https://h10057.www1.hp.com/ecomcat/hpcatalog/specs/provisioner/99/Q8411A.htm](https://h10057.www1.hp.com/ecomcat/hpcatalog/specs/provisioner/99/Q8411A.htm)

Implies that Hplip supports this model, so I upgraded successfully to 3.9.4b. Still does not find the printer.

Output from hp-setup below:

userabc@mediacenter:/home/temp$ hp-setup

HP Linux Imaging and Printing System (ver. 3.9.4b)
Printer/Fax Setup Utility ver. 9.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP

output of hp-check below:

root@mediacenter:/proc# hp-check

HP Linux Imaging and Printing System (ver. 3.9.4b)
Dependency/Version Check Utility ver. 14.3

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Note: hp-check can be run in three modes:
1. Compile-time check mode (-c or --compile): Use this mode before compiling the HPLIP supplied tarball (.tar.gz or .run) to
determine if the proper dependencies are installed to successfully compile HPLIP.
2. Run-time check mode (-r or --run): Use this mode to determine if a distro supplied package (.deb, .rpm, etc) or an already
built HPLIP supplied tarball has the proper dependencies installed to successfully run.
3. Both compile- and run-time check mode (-b or --both) (Default): This mode will check both of the above cases (both compile-
and run-time dependencies).

Saving output in log file: hp-check.log

Initializing. Please wait...

---------------
| SYSTEM INFO |
---------------

Basic system information:
Linux mediacenter 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

Distribution:
ubuntu 9.04

HPOJ running?
No, HPOJ is not running (OK).

Checking Python version...
OK, version 2.6.2 installed

Checking PyQt 4.x version...
OK, version 4.4.4 installed.

Checking for CUPS...
Status: scheduler is running
Version: 1.3.9
error_log is set to level: warn

Checking for dbus/python-dbus...
dbus daemon is running.
python-dbus version: 0.83.0

------------------------------------
| COMPILE AND RUNTIME DEPENDENCIES |
------------------------------------

note: To check for compile-time only dependencies, re-run hp-check with the -c parameter (ie, hp-check -c).
note: To check for run-time only dependencies, re-run hp-check with the -r parameter (ie, hp-check -r).

Checking for dependency: CUPS - Common Unix Printing System...
OK, found.

Checking for dependency: CUPS DDK - CUPS driver development kit...
OK, found.

Checking for dependency: CUPS devel- Common Unix Printing System development files...
OK, found.

Checking for dependency: CUPS image - CUPS image development files...
OK, found.

Checking for dependency: DBus - Message bus system...
OK, found.

Checking for dependency: gcc - GNU Project C and C++ Compiler...
OK, found.

Checking for dependency: GhostScript - PostScript and PDF language interpreter and previewer...
OK, found.

Checking for dependency: libcrypto - OpenSSL cryptographic library...
OK, found.

Checking for dependency: libjpeg - JPEG library...
OK, found.

Checking for dependency: libnetsnmp-devel - SNMP networking library development files...
OK, found.

Checking for dependency: libpthread - POSIX threads library...
OK, found.

Checking for dependency: libtool - Library building support services...
OK, found.

Checking for dependency: libusb - USB library...
OK, found.

Checking for dependency: make - GNU make utility to maintain groups of programs...
OK, found.

Checking for dependency: PIL - Python Imaging Library (required for commandline scanning with hp-scan)...
OK, found.

Checking for dependency: PolicyKit - Administrative policy framework...
warning: NOT FOUND! This is an OPTIONAL/RUNTIME ONLY dependency. Some HPLIP functionality may not function properly.

Checking for dependency: ppdev - Parallel port support kernel module....
OK, found.

Checking for dependency: PyQt 4 DBus - DBus Support for PyQt4...
OK, found.

Checking for dependency: Python ctypes - A foreign function library for Python...
OK, found.

Checking for dependency: Python DBus - Python bindings for DBus...
OK, found.

Checking for dependency: Python devel - Python development files...
OK, found.

Checking for dependency: Python XML libraries...
OK, found.

Checking for dependency: Python 2.3 or greater - Required for fax functionality...
OK, found.

Checking for dependency: Python 2.2 or greater - Python programming language...
OK, found.

Checking for dependency: Reportlab - PDF library for Python...
OK, found.

Checking for dependency: SANE - Scanning library...
OK, found.

Checking for dependency: SANE - Scanning library development files...
OK, found.

Checking for dependency: scanimage - Shell scanning program...
OK, found.

Checking for dependency: xsane - Graphical scanner frontend for SANE...
OK, found.

----------------------
| HPLIP INSTALLATION |
----------------------

Currently installed HPLIP version...
HPLIP 3.9.4b currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf. Generated from hplip.conf.in by configure.

[hplip]
version=3.9.4b

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/hpijs/HP
ppdbase=/usr/share/ppd/hpijs
doc=/usr/share/doc/hplip-3.9.4b
icon=/usr/share/applications
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv/hp/

# Following values are determined at configure time and cannot be changed.
[configure]
network-build=yes
pp-build=no
gui-build=yes
scanner-build=yes
fax-build=yes
dbus-build=yes
cups11-build=no
doc-build=yes
shadow-build=no
foomatic-drv-install=yes
foomatic-ppd-install=no
foomatic-rip-hplip-install=no
cups-ppd-install=no
cups-drv-install=no
internal-tag=3.9.4b.10
restricted-build=no
ui-toolkit=qt4
qt3=no
qt4=yes
policy-kit=yes

Current contents of '/var/lib/hp/hplip.state' file:
# hplip.state - HPLIP runtime persistent variables.

[plugin]
installed=0
eula=0

Current contents of '~/.hplip/hplip.conf' file:
[installation]
date_time = 06/08/09 21:57:17
version = 3.9.4b

--------------------------
| DISCOVERED USB DEVICES |
--------------------------

No devices found.

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

warning: No queues found.

----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
OK, found. SANE backend 'hpaio' is properly set up.

Checking output of 'scanimage -L'...

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

---------------------
| PYTHON EXTENSIONS |
---------------------

Checking 'cupsext' CUPS extension...
OK, found.

Checking 'pcardext' Photocard extension...
OK, found.

Checking 'hpmudext' I/O extension...
OK, found.

Checking 'scanext' SANE scanning extension...
OK, found.

-----------------
| USB I/O SETUP |
-----------------

Checking for permissions of USB attached printers...

HP Device 0x7411 at 001:008:
    Device URI: hp:/usb/Photosmart_C4600_series?serial=CN93DCF0GK05BQ
    Device node: /dev/bus/usb/001/008
    Mode: 0660
getfacl: Removing leading '/' from absolute path names
# file: dev/bus/usb/001/008
# owner: lp
# group: lp
user::rw-
user:tv:rw-
group::rw-
mask::rw-
other::---

---------------
| USER GROUPS |
---------------

root

-----------
| SUMMARY |
-----------

error: 1 error or warning.

Please refer to the installation instructions at:
[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)

Done.

This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Searching... (bus=usb, search=(None) desc=0)
error: No devices found on bus: usb

Done.




I also posted this problem to the HPLIP forum page.

---

### Post by ewr2san on 2009-06-09
Here's the answer that I got from HPLIP developers:

The Photosmart C4600 series printers are not yet supported by HPLIP.
They will be support in a future upcoming release of HPLIP.

Sorry for the inconvenience.

Thanks for your support of HPLIP--we appreciate it.

---

### Post by ewr2san on 2009-06-22
hplip 3.9.6 supports the printer nicely.

The hplip website mistakenly tells you that 3.9.4 supports it (not true), check the release notes.  It also tells you that you have to compile support (again not true).

Find the hplip-3.9.6.run 
[http://prdownloads.sourceforge.net/hplip/hplip-3.9.6.run](http://prdownloads.sourceforge.net/hplip/hplip-3.9.6.run)

chmod 755 hplip-3.9.6.run

and run it (./hplip-3.9.6.run).  

Guides you through the install, and leaves you with a working printer!

---

### Post by ewr2san on 2010-01-06
The later versions of HPLIP also support this well.. Just upgraded to HPLIP 3.9.8 and it still works perfectly.

---

### Post by Eliser on 2010-04-21
> **ewr2san said:**
> hplip 3.9.6 supports the printer nicely.

The hplip website mistakenly tells you that 3.9.4 supports it (not true), check the release notes.  It also tells you that you have to compile support (again not true).

Find the hplip-3.9.6.run 
[http://prdownloads.sourceforge.net/hplip/hplip-3.9.6.run](http://prdownloads.sourceforge.net/hplip/hplip-3.9.6.run)

chmod 755 hplip-3.9.6.run

and run it (./hplip-3.9.6.run).  

Guides you through the install, and leaves you with a working printer!


Hi there, I'm new in Ubuntu 9.04, I need to install my new HP Photosmart C4600 and as far as I understand, hplip 3.9.6.run supports it. I've followed your indications and the download is done. Now, I need to choose a programme to open it and I have no idea which one would do it.

Could you help me? That would be great.

Eliser

---

