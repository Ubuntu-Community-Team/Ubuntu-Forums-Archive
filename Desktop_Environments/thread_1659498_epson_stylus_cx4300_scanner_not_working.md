---
title: "epson stylus cx4300 scanner not working"
date: 2011-01-04
forum: Desktop Environments
---

### Post by ilantal on 2011-01-04
Hi Community,
I have an Epson CX4300 on Ubuntu 10.10 and I can't get it to scan. I loaded the driver for CX4200 since CX4300 isn't listed in
[http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escpr/](http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escpr/)

sane-find-scanner finds the scanner but scanimage doesn't:
ilan@ilan-main:~$ sane-find-scanner -q
found USB scanner (vendor=0x04b8, product=0x083f) at libusb:003:002
ilan@ilan-main:~$ scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

XSane also reports No Devices available and number 4 in their possible reasons is The backend is not loaded by SANE (man sane-dll). I get:
ilan@ilan-main:~$ man sane-dll
No manual entry for sane-dll

I do get a man for sane-epson so that hints that the epson driver exists. The fact that sane-dll doesn't seem to exist is probably the problem. I'm using libsane in the Synaptic Package Manager and that is supposed to supply the backends. Should it include sane-dll?

I need some fresh input from anyone who might be able to help.
Thanks,
Ilan

---

### Post by peterop on 2011-01-05
Hi

 I have an Epson Perfection 4490 Photo scanner
that has been working fine on my Ubuntu system for years.
I do not use the scanner that much so I am not sure when it 
stopped working but it now does not respond in a similar way
to Ian's cx4300 scanner. My system is dual boot to Windows XP
so I know the scanner still works okay. I upgraded to Ubuntu 10.10 in November and the scanner was working fine after the 
upgrade.

$ sane-find-scanner -q
found USB scanner (vendor=0x04b8 [EPSON], product=0x0119 [EPSON Scanner]) at libusb:001:004

% scanimage -L

No scanners were identified. If you were expecting something different,check that the scanner is plugged in, turned on and detected by the sane-find-scanner tool (if appropriate). Please read the documentation which came with this software (README, FAQ, manpages).


-regards peterop

---

### Post by peterop on 2011-01-10
As noted from my previous post I have been using
my Epson Perfection 4490 Photo Scanner for years
on Ubuntu with little problems.
It has stopped working in the last few weeks.
I mainly use the "iscan" or "Xsane" programs.

 I found a reference to a problem with "iscan" and
a new Debian package on the Avasys web site.

[http://avasys.jp/eng/linux_driver/faq/id000837.php](http://avasys.jp/eng/linux_driver/faq/id000837.php)

 The package seems to have  broken "iscan" and "Xsane" so an upgrade
of "iscan" is needed. The Debian packages (3) can be downloaded
from "http://avasys.jp/eng/linux_driver/download/".

 I already have the (libsane, libsane-extras, sane, sane-utils, xsane,
xsane-common) packages installed.

 There are 3 "iscan" packages needed for my scanner .
There is 2 sets of the "iscan" and "iscan-plugin" packages depending
if your system has the "libltdl3" or "libltdl7" package installed.
I have the "libltdl7" package installed.

Downloaded packages:
 deb package
 iscan-data_1.6.0-0_all.deb

 deb 32bit package [libltdl7] (for Ubuntu 8.10 or later)
 iscan_2.26.1-3.ltdl7_i386.deb   351,988 bytes
 iscan-plugin-gt-x750_2.1.0-5_i386.deb


Install packages:

 dpkg -i iscan-data_1.6.0-0_all.deb
 dpkg -i iscan_2.26.1-3.ltdl7_i386.deb
 dpkg -i iscan-plugin-gt-x750_2.1.0-5_i386.deb


 My scanner is back working. "iscan" and "Xsane" are working fine.

 Some control files were already setup on my system.

#add "epkowa" and comment out "epson"!
 sudo gedit /etc/sane.d/dll.conf

# Check for printer info

 sane-find-scanner -q
found USB scanner (vendor=0x04b8 [EPSON], product=0x0119 [EPSON Scanner]) at libusb:001:002

#Edit "/etc/udev/libsane-extras.rules"
Add:

# Epson Perfection 4490
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0119", MODE="664", GROUP="scanner"


-peterp

---

### Post by ilantal on 2011-01-18
Thanks for the input. Things have improved, but the scanner is not yet working. Yesterday it would scan ONE page, but today it is back to ZERO pages. To get it to scan ONE page I had to do a reboot, but that doesn't seem to work anymore.

I had found independently that YES, it is VERY important which driver one uses.
dpkg -i iscan-data_1.6.0-0_all.deb
dpkg -i iscan_2.26.1-3.ltdl7_i386.deb

The above 2 drivers are correct with Ubuntu 8.10 and beyond. I was using an older one WITHOUT ltdl7 and it won't work with Ubuntu 10.10. I used a plugin compatible with the cx4300 which is different from yours.

After I updated drivers the scanImage -L started to recognize my scanner. Now I think my problem is with the non existent scanner group.

I used
sudo gedit /etc/udev/rules.d/45-libsane.rules

where I put
# Epson CX4300
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="083f", MODE="664", OWNER="lp", GROUP="scanner"

but there is no group called scanner, so it makes no sense to add the above line. In any case, I'm still stuck and would appreciate some more advice.

Thanks,
Ilan

---

### Post by peterop on 2011-01-22
I believe one of the sane packages will create the 
scanner group.  I have the (libsane, libsane-extras, sane, sane-utils, xsane, xsane-common) packages installed.

 You could create the group with:

 addgroup scanner

 Then add yourself to that group.
My group looks like the following:

scanner:x:105:hplip,visitor

-peterop

---

### Post by ilantal on 2011-01-25
Hi Peterop,
Thanks for your help. Today I got it to scan 2 pages, but I had to log off between scans.
I did manage to create the scanner group but it didn't help. The problem doesn't seem to be with the lack of that group.
I thought it might be that I need to use sudo iscan, but that too wasn't the problem.
It seems to be the driver itself has problems because ALWAYS after the first scan it gives an error message. Sometimes pressing the Stop button and then turning off the cx4300 helps and sometimes not.
It is extremely unreliable. After the first scan (if even the first scan works), I have to exit the printer and Ubuntu. Something seems to get "stuck" in the system, probably as a result of the incomplete scan. It looks to me to be an incompatibility between the driver and the cx4300.

I don't need it that often, so I'll just hope it works when I really need it. Not very scientific but I have no real solution.

Ilan

---

### Post by peterop on 2011-02-04
Hi 

 I was away so could not reply to your problem.

 I noticed that the CX4300 driver listed in the
second part of the AVASYS driver page. Select the driver and OS
then continue into the next page.

	 Epson Stylus CX4300/CX4400/CX4450/CX5500/CX5600/DX4400/DX4450


[http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do)

-peterop

---

