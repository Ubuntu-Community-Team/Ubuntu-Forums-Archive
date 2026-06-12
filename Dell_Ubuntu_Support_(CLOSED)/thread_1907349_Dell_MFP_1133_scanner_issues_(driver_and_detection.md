---
title: "Dell MFP 1133 scanner issues (driver and detection)"
date: 2012-01-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Chani.xy on 2012-01-11
Hello,

I'm having troubles with the scanner Dell 1133 on Ubuntu 11.10. I have 2 related issues :

1) Cannot properly install Dell unified driver
2) Scanner is not detected by Dell software (but there is a way to get it detected by simple-scan, see below)

1) The dell unified driver installer crashes when launched from graphical desktop environment (tried with unity, unity2D, gnome shell, gnome classic, gnome classic no effects) : in all cases, the desktop logs me out and returns to login screen during install.
Note: it first complains that SANE is not installed (but it is, so i click on install anyway and it crashes afterwards).

I can however install using a virtual terminal (ctrl+alt+f1), but there are some errrors during install. Here's the log for sudo ./install.sh

```

****  It seems Qt library is not installed, or X display is not accessible.
****  Custom Qt library will be configured for use with this package.
GUI mode installer execution failed, proceeding in text mode
****  Running text mode install
****  Press Enter to continue or q and then Enter to quit: 
****  Print drivers for the following device models available:
dp1130n dp1130 dp5330 mfp1133 mfp1815ps mfp2145ps mfp2335ps
****  Please enter model to install and press Enter: mfp1133
INFO: Restarting udev ...
Usage: udevadm [--help] [--version] [--debug] COMMAND [COMMAND OPTIONS]
  info         query sysfs or the udev database
  trigger      request events from the kernel
  settle       wait for the event queue to finish
  control      control the udev daemon
  monitor      listen to kernel and udev events
  test         simulation run

control: unrecognized option '--reload_rules'
INFO: Installing MFP port and SANE backend libraries ...
INFO: Installing GUI lpr ...
INFO: Fixing file ownership and permissions ...
INFO: Registering SANE backend ...
INFO: Registering CUPS printer ...
cp: impossible d'évaluer «/opt/DELL/mfp/share/ppd/cms/*»: Aucun fichier ou dossier de ce type
chmod: impossible d'accéder à «/usr/share/cups/model/dell/cms/*»: Aucun fichier ou dossier de ce type
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service cups restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) and then start(8) utilities,
e.g. stop cups ; start cups. The restart(8) utility is also available.
cups stop/waiting
cups start/running, process 8514
INFO: CUPS restart OK
INFO: Creating menu entries ...
mkdir: impossible de créer le répertoire «/proc/Desktop»: Aucun fichier ou dossier de ce type
chmod: impossible d'accéder à «/proc/Desktop»: Aucun fichier ou dossier de ce type
chown: impossible d'accéder à «/proc/Desktop»: Aucun fichier ou dossier de ce type
mkdir: impossible de créer le répertoire «/proc/.gnome-desktop»: Aucun fichier ou dossier de ce type
chmod: impossible d'accéder à «/proc/.gnome-desktop»: Aucun fichier ou dossier de ce type
chown: impossible d'accéder à «/proc/.gnome-desktop»: Aucun fichier ou dossier de ce type
[: 1870: Illegal number: 
/opt/DELL/PSU/share/en
INFO: psu (ver.3.00.05) has been installed successfully in /opt/DELL/PSU
INFO: phonebook (ver.3.00.05) has been installed successfully in /opt/DELL/PhoneBook
INFO: emailbook (ver.3.00.05) has been installed successfully in /opt/DELL/EmailBook
INFO: addressbook (ver.3.00.05) has been installed successfully in /opt/DELL/AddressBook
INFO: wirelesssetup (ver.3.00.05) has been installed successfully in /opt/DELL/WirelessSetup
INFO: Shutting down psulauncher: 
INFO: psulauncher (ver.2.00.57) has been installed successfully in /opt/DELL/PSULauncher
INFO: Starting psulauncher ...
INFO: Finishing installation ...
****  Text mode install finished

```2) However, when launching the Dell Driver Configurator, the scanner is not detected (yes, it is plugged in and turned on).

There's a check_installation script with the drivers, here's the output :

```

drwxr-xr-x 2 root root 4096 2012-01-10 12:02 /usr/share/cups/model/dell/cms
-r--r--r-- 1 root root 5029 2012-01-11 13:06 /usr/share/cups/model/dell/dp1130n.ppd.gz
-r--r--r-- 1 root root 4858 2012-01-11 13:06 /usr/share/cups/model/dell/dp1130.ppd.gz
-r--r--r-- 1 root root 8293 2012-01-11 13:06 /usr/share/cups/model/dell/dp5330.ppd.gz
-r--r--r-- 1 root root 4570 2012-01-11 13:06 /usr/share/cups/model/dell/mfp1133.ppd.gz
-r--r--r-- 1 root root 4722 2012-01-11 13:06 /usr/share/cups/model/dell/mfp1815ps.ppd.gz
-r--r--r-- 1 root root 8008 2012-01-11 13:06 /usr/share/cups/model/dell/mfp2145ps.ppd.gz
-r--r--r-- 1 root root 6293 2012-01-11 13:06 /usr/share/cups/model/dell/mfp2335ps.ppd.gz
lrwxrwxrwx 1 root root    11 2012-01-11 13:07 /usr/lib64/libmfp.so -> libmfp.so.1
lrwxrwxrwx 1 root root    15 2012-01-11 13:07 /usr/lib64/libmfp.so.1 -> libmfp.so.1.0.1
-rwxrwxrwx 1 root root 29584 2009-09-03 16:25 /usr/lib64/libmfp.so.1.0.1
-rwxrwxrwx 1 root root 19968 2009-09-03 16:25 /usr/lib64/cups/backend/mfp
-rwxr-xr-x 1 root root 19968 2009-09-03 16:25 /usr/lib/cups/backend/mfp
-rwxr-xr-x 1 root root  52824 2009-09-04 07:28 /usr/lib64/cups/filter/rastertosamsunginkjet
-rwxr-xr-x 1 root root  32752 2009-09-04 07:28 /usr/lib64/cups/filter/rastertosamsungpcl
-rwxr-xr-x 1 root root  56720 2009-09-04 07:28 /usr/lib64/cups/filter/rastertosamsungspl
-rwxr-xr-x 1 root root 147504 2009-09-04 07:28 /usr/lib64/cups/filter/rastertosamsungsplc
-rwxr-xr-x 1 root root  52824 2009-09-04 07:28 /usr/lib/cups/filter/rastertosamsunginkjet
-rwxr-xr-x 1 root root  32752 2009-09-04 07:28 /usr/lib/cups/filter/rastertosamsungpcl
-rwxr-xr-x 1 root root  56720 2009-09-04 07:28 /usr/lib/cups/filter/rastertosamsungspl
-rwxr-xr-x 1 root root 147504 2009-09-04 07:28 /usr/lib/cups/filter/rastertosamsungsplc
-rwxr-xr-x 1 root root 32568 2009-09-04 07:28 /usr/lib64/cups/filter/smfpautoconf
-rwxr-xr-x 1 root root 32568 2009-09-04 07:28 /usr/lib/cups/filter/smfpautoconf
-rwxrwxrwx 1 root root 11144 2009-09-04 07:28 /usr/lib64/cups/filter/pscms
-rwxrwxrwx 1 root root 11144 2009-09-04 07:28 /usr/lib/cups/filter/pscms
lrwxrwxrwx 1 root root     17 2012-01-11 13:07 /usr/lib64/sane/libsane-smfp.so -> libsane-smfp.so.1
lrwxrwxrwx 1 root root     21 2012-01-11 13:07 /usr/lib64/sane/libsane-smfp.so.1 -> libsane-smfp.so.1.0.1
-rwxrwxrwx 1 root root 398928 2009-07-09 14:45 /usr/lib64/sane/libsane-smfp.so.1.0.1
lrwxrwxrwx 1 root root    27 2012-01-08 18:38 /usr/lib/sane/libsane-xerox_mfp.so.1 -> libsane-xerox_mfp.so.1.0.22
-rw-r--r-- 1 root root 68288 2011-09-22 15:12 /usr/lib/sane/libsane-xerox_mfp.so.1.0.22
-rw-r--r-- 1 root root 869 2011-09-22 15:12 /etc/sane.d/xerox_mfp.conf
-rw-r--r-- 1 root root 1125 2012-01-11 13:07 /etc/sane.d/smfp.conf
/etc/sane.d/dll.conf:xerox_mfp
/etc/sane.d/dll.conf:smfp

```I believe the sane backend that is being added is smfp.conf and/or xerox_mfp. I do find strange however that the model that is given inside these files is not the 1133 but the 1815. Here's the content of smfp.conf :

```

?xml version="1.0"?>
<smfpconfig>
  <option name="network" type="enum">yes</option>
    <option name="network" type="enum">yes</option>
    <option name="network" type="enum">yes</option>
    <option name="network" type="enum">yes</option>
    <model vendor="dell" id="mfp1815" modelstring="Laser MFP 1815">
        <hwoption name="twainspec" type="enum">3</hwoption>
        <hwoption name="sleep_after_scan_ms" type="int">2000</hwoption>
        <hwoption name="adf" type="enum">simplex</hwoption>
        <hwoption name="flatbed" type="enum">yes</hwoption>
        <hwoption name="resolution" type="list" default="300">75 100 150 200 300 600</hwoption>
        <hwoption name="colorcompose" type="list" default="color24bit">color24bit gray256 bw_halftone bw_lineart</hwoption>
        <hwoption name="pageformat" type="list" default="a4">
            a4 letter legal statement folio
            a5 a5_extra b5 b5_extra b5_jis
            executive quatro letter_plus a4_plus
            envelope_9 envelope_10 envelope_11 envelope_12
            envelope_14 envelope_b5 envelope_b6 envelope_c5
            envelope_c6 envelope_c6c5 envelope_dl
            envelope_110x230 envelope_monarch
            custom
        </hwoption>
    </model>
</smfpconfig>

```and xerox_mfp.conf contains :
```

#Dell Laser MFP 1815cn
usb 0x413c 0x5124

```Finally, some sane info. Here's the output from sane-find-scanner :

```

found USB scanner (vendor=0x413c [Dell], product=0x5321 [1133 Laser MFP]) at libusb:001:008

```edit: Hearing only my intuition, i added the following line to xerox_mfp.conf :

```

usb 0x413c 0x5321

```With this, simple-scan finds the scanner (and it works!). However the dell unified driver configurator still doesn't find it. I don't understand why.
Maybe I should also add the 1133 to smfp.conf (it seems like the install didn't get that i had 1133), but i don't know what to add there.

What does the Dell unfiied driver add anyway ? (toner maintenance, etc. ?) Can I just simply uninstall it and add the usb vendor model line to xerox_mfp ?

I don't know what to do further. Any help appreciated !

---

### Post by Chani.xy on 2012-01-20
Little bump. Any insights ?

---

### Post by jleyaoua on 2012-01-24
Hello, 

My configuration seems to be similar, and I have got the same problem. I am using Ubuntu 11.10 with the Dell 1133 multifunction printer. 

I could not install the printer with the ./install.sh provided with the Dell installation CD.  During the install process, I am logged out and I returns to the login screen. 

The printer was consequently installed with the Ubuntu GUI, and it works well. 

However, I am not able to use the scanner of the Dell 1133 multifunction printer. The Dell software warns me that he can not detect a scanner (SANE is installed and of course the printer is on). 

Any ideas to resolve this issue ? thanks,

---

