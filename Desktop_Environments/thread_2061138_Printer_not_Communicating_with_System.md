---
title: "Printer not Communicating with System"
date: 2012-09-21
forum: Desktop Environments
---

### Post by Alcidious on 2012-09-21
So I have an HP Officejet 4620, am running Ubuntu 12.04 32-bit on a Desktop, and for some reason when I try to use the printer I get the following: "HPLIP Device Status, Officejet_4620_series (CN23S1332905RT) Device Communication Error (5012)"

But the hplip troubleshooting documentation is not very helpful.  I can't locate the error.  Any ideas?

---

### Post by confusedstingray on 2012-09-21
2 things
the hp's i had, they had to be turn on first them my machine and they worked
why don’t know. turn them on after machine was up trouble,

also have you tried to set the printer up with out using the hp setup 
try installing it manually 
my samsung did the same thing had a linux setup for ubuntu 
but didn't work,
removed the setup and went through the printing tab and add
and it works fine,

---

### Post by Alcidious on 2012-09-21
I might just try removing everything and then doing a reinstall, perhaps trying to do it manually first.  After viewing the output of hp-check -t I remembered the printer quit working one day after it ran out of ink.  I changed out the cartridges and it hasn't worked since. Weird!

Heres the output:


alcidious25@extremis:~$ hp-check -t

HP Linux Imaging and Printing System (ver. 3.12.6)
Dependency/Version Check Utility ver. 15

Copyright (c) 2001-14 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Note: hp-check can be run in three modes:
1. Compile-time check mode (-c or --compile): Use this mode before compiling the
HPLIP supplied tarball (.tar.gz or .run) to determine if the proper dependencies
are installed to successfully compile HPLIP.                                    
2. Run-time check mode (-r or --run): Use this mode to determine if a distro    
supplied package (.deb, .rpm, etc) or an already built HPLIP supplied tarball   
has the proper dependencies installed to successfully run.                      
3. Both compile- and run-time check mode (-b or --both) (Default): This mode    
will check both of the above cases (both compile- and run-time dependencies).   

Check types:                                                                    
a. EXTERNALDEP - External Dependencies                                          
b. GENERALDEP - General Dependencies (required both at compile and run time)    
c. COMPILEDEP - Compile time Dependencies                                       
d. [All are run-time checks]                                                    
PYEXT SCANCONF QUEUES PERMISSION                                                

Status Types:
    OK
    MISSING       - Missing Dependency or Permission or Plug-in
    INCOMPAT      - Incompatible dependency-version or Plugin-version

Saving output in log file: /home/alcidious25/hp-check.log

Initializing. Please wait...
 
---------------
| SYSTEM INFO |
---------------

 Kernel: 3.2.0-30-generic-pae #48-Ubuntu SMP Fri Aug 24 17:14:09 UTC 2012 GNU/Linux
 Host: extremis
 Proc: 3.2.0-30-generic-pae #48-Ubuntu SMP Fri Aug 24 17:14:09 UTC 2012 GNU/Linux
 Distribution: ubuntu 12.04

-----------------------
| HPLIP CONFIGURATION |
-----------------------

HPLIP-Version: HPLIP 3.12.6
HPLIP-Home: /usr/share/hplip
HPLIP-Installation: Auto installation is supported for ubuntu distro  12.04 version 

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.12.6

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/HP
ppdbase=/usr/share/ppd
doc=/usr/share/doc/hplip-3.12.6
icon=/usr/share/applications
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv/hp

# Following values are determined at configure time and cannot be changed.
[configure]
network-build=yes
libusb01-build=no
pp-build=no
gui-build=yes
scanner-build=yes
fax-build=yes
dbus-build=yes
cups11-build=no
doc-build=yes
shadow-build=no
hpijs-install=no
foomatic-drv-install=no
foomatic-ppd-install=no
foomatic-rip-hplip-install=no
hpcups-install=yes
cups-drv-install=yes
cups-ppd-install=no
internal-tag=3.12.6
restricted-build=no
ui-toolkit=qt4
qt3=no
qt4=yes
policy-kit=no
hpijs-only-build=no
lite-build=no
udev-acl-rules=yes
udev_sysfs_rules=no
hpcups-only-build=no
hpijs-only-build=no


Current contents of '/var/lib/hp/hplip.state' file:
Plugins are not installed. Could not access file: No such file or directory

Current contents of '~/.hplip/hplip.conf' file:
[installation]
date_time = 09/21/2012 18:59:34
version = 3.12.6

[upgrade]
notify_upgrade = false
last_upgraded_time = 1346773217
pending_upgrade_time = 0
latest_available_version = 3.12.9

[settings]
systray_visible = 0
systray_messages = 0

[last_used]
device_uri = "hpfax:/usb/Officejet_4620_series?serial=CN23S1332905RT"
printer_name = 
working_dir = .

[commands]
scan = /usr/bin/xsane -V %SANE_URI%

[refresh]
rate = 30
enable = false
type = 1

[polling]
enable = false
interval = 5
device_list = 

[fax]
voice_phone = 
email_address = 


 <Package-name>        <Package-Desc>      <Required/Optional> <Min-Version> <Installed-Version> <Status>   <Comment>

--------------------------
|  External Dependencies |
--------------------------

 gs                   Ghostscript               REQUIRED        7.05            9.05            OK         -
 network              Network-wget              OPTIONAL        -               1.13.4          OK         -
 dbus                 DBus                      REQUIRED        -               1.4.18          OK         -
 scanimage            Shell-Scanning            OPTIONAL        1.0             1.0.22          OK         -
 policykit            Admin-Policy-framework    OPTIONAL        -               0.104           OK         -
 xsane                SANE-GUI                  OPTIONAL        0.9             0.998           OK         -
 cups                 CUPS                      REQUIRED        1.1             1.5.3           OK         'CUPS Scheduler is running'

-------------------------
|  General Dependencies |
-------------------------

 reportlab            Python-PDF-Lib            OPTIONAL        2.0             2.5             OK         -
 libcrypto            OpenSSL-Crypto-Lib        REQUIRED        -               1.0.1           OK         -
 pil                  Python-Image-Lib          OPTIONAL        -               1.1.7           OK         -
 pyqt4-dbus           PyQt4-DBUS                REQUIRED        4.0             4.9.1           OK         -
 libjpeg              JPEG-Lib                  REQUIRED        -               -               OK         -
 libpthread           POSIX-Threads-Lib         REQUIRED        -               2.15            OK         -
 python-dbus          Python-DBUS               REQUIRED        0.80.0          1.0.0           OK         -
 python-devel         Python-SDK                REQUIRED        2.2             2.7.3           OK         -
 pyqt4                Python-Qt4                REQUIRED        4.0             4.9.1           OK         -
 cups-devel           CUPS-SDK                  REQUIRED        -               1.5.3           OK         -
 sane-devel           SANE-SDK                  REQUIRED        -               1.0.22          OK         -
 libusb               USB-Lib                   REQUIRED        -               1.0             OK         -
 sane                 Scan-Lib                  REQUIRED        -               1.0.22          OK         -
 cups-image           CUPS-Image-Lib            REQUIRED        -               1.5.3           OK         -
 libnetsnmp-devel     SNMP-Networking-SDK       REQUIRED        5.0.9           5.4.3           OK         -
 python-xml           Python-XML-Lib            REQUIRED        -               2.0.1           OK         -
 python-notify        Desktop-notifications     OPTIONAL        -               -               OK         -

------------------------------
|  Compile Time Dependencies |
------------------------------

 gcc                  gcc-Compiler              REQUIRED        -               4.6.3           OK         -
 libtool              Build-tools               REQUIRED        -               2.4.2           OK         -
 make                 GNU-Build-tools           REQUIRED        3.0             3.81            OK         -

----------------------
|  Python Extentions |
----------------------

 cupsext              CUPS-Extension            REQUIRED        -               3.12.6          OK         -
 pcardext             PhotoCard-Extension       REQUIRED        -               3.12.6          OK         -
 hpmudext             IO-Extension              REQUIRED        -               3.12.6          OK         -

-----------------------
|  Scan Configuration |
-----------------------

 hpaio                HPLIP-SANE-Backend        REQUIRED        -               3.12.6          OK         'hpaio found in /etc/sane.d/dll.conf'
 scanext              Scan-SANE-Extension       REQUIRED        -               3.12.6          OK         -

------------------------------
| DISCOVERED SCANNER DEVICES |
------------------------------

No Scanner found.

--------------------------
| DISCOVERED USB DEVICES |
--------------------------

No devices found.

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
Officejet_4620
--------------
Type: Printer
Device URI: hp:/usb/Officejet_4620_series?serial=CN23S1332905RT
PPD: /etc/cups/ppd/Officejet_4620.ppd
PPD Description: HP Officejet 4620 Series, hpcups 3.12.6
Printer status: printer Officejet_4620 disabled since Tue 04 Sep 2012 11:22:03 AM EDT - Unplugged or turned off
error: Unable to communicate with device (code=12): hp:/usb/Officejet_4620_series?serial=CN23S1332905RT
error: Device not found
error: Communication status: Failed

Officejet_4620_2
----------------
Type: Printer
Device URI: hp:/usb/Officejet_4620_series?serial=CN23S1332905RT
PPD: /etc/cups/ppd/Officejet_4620_2.ppd
PPD Description: HP Officejet j4660 Series, hpcups 3.12.6
Printer status: printer Officejet_4620_2 disabled since Tue 04 Sep 2012 11:22:03 AM EDT Unplugged or turned off
error: Unable to communicate with device (code=12): hp:/usb/Officejet_4620_series?serial=CN23S1332905RT
error: Device not found
error: Communication status: Failed

Officejet_4620_fax
------------------
Type: Fax
Device URI: hpfax:/usb/Officejet_4620_series?serial=CN23S1332905RT
PPD: /etc/cups/ppd/Officejet_4620_fax.ppd
PPD Description: HP Fax hpcups
Printer status: printer Officejet_4620_fax disabled since Tue 04 Sep 2012 11:22:03 AM EDUnplugged or turned off
error: Unable to communicate with device (code=12): hpfax:/usb/Officejet_4620_series?serial=CN23S1332905RT
error: Device not found
error: Communication status: Failed

Officejet_4620_fax_2
--------------------
Type: Fax
Device URI: hpfax:/usb/Officejet_4620_series?serial=CN23S1332905RT
PPD: /etc/cups/ppd/Officejet_4620_fax_2.ppd
PPD Description: HP Fax4 hpcups
Printer status: printer Officejet_4620_fax_2 disabled since Tue 04 Sep 2012 11:22:03 AM Unplugged or turned off
error: Unable to communicate with device (code=12): hpfax:/usb/Officejet_4620_series?serial=CN23S1332905RT
error: Device not found
error: Communication status: Failed


--------------
| PERMISSION |
--------------

groups          user-groups                    Required        -        -        OK       alcidious25 adm lp cdrom sudo audio dip video plugdev lpadmin pulse pulse-access sambashare

 
-----------
| SUMMARY |
-----------

Missing Required Dependencies
-----------------------------
None

Missing Optional Dependencies
-----------------------------
None


Total Errors: 4
Total Warnings: 0


Done.
alcidious25@extremis:~$

---

### Post by Frogs Hair on 2012-09-22
When I installed my all in one I added the HPLIP toolbox GUI from The software center . In the application there is a place to check supplies/ink and it displays ink level. If the cartridges were not seated properly it will be displayed .

Have you restarted the printer since adding the new cartridges? I would also double check the procedure for adding cartridges there may be something you need to do with the printer controls.You can get a manual here if needed.         

[http://www.manualowl.com/p/Hewlett-Packard/Officejet-4620/Manual/162050](http://www.manualowl.com/p/Hewlett-Packard/Officejet-4620/Manual/162050)

---

