---
title: "HP Scanjet 3670 driver"
date: 2009-03-06
forum: General Help
---

### Post by onemile on 2009-03-06
I've done a bit of serching and all i found out is that there is no driver available for this scaner.

Is there realy no workaround to make this scanner work on ubuntu?

---

### Post by LegendofTom on 2009-03-06
I did some searching too, and it seems you are out of luck.

---

### Post by onemile on 2009-03-08
Ok, I'll throw it away...
Tnx, for info

---

### Post by Almoz on 2009-05-26
Hello,

Anybody pls help about this scanner, it could be that driver for some hp scanjet 36** series should work?

Actually we I do not need full functionality of this hp, just black and white could be enough!

Pls help

---

### Post by Gaming4JC on 2010-04-25
Just got an hpscanjet 3670 and tried it on Karmic, it's not being detected even via lsusb... any ideas?

---

### Post by desertdog on 2010-04-25
This scanner is now supported by Sane. You have to download the latest source code and compile it. 

See [http://mp610.blogspot.com/2008_04_01_archive.html](http://mp610.blogspot.com/2008_04_01_archive.html) for a good guide on how to do this. 

Basically you need to do:
$sudo apt-get install git
$sudo apt-get install libsane-dev
$cd ~
$ git clone git://git.debian.org/sane/sane-backends.git
$cd sane-backends
$ ./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var
$make
$sudo make install
Then hopefully your scanner will show up after:
$scanimage -L

Good luck

---

### Post by mtphr on 2010-10-07
this still doesn't work for me.

lsusb still shows the scanner. (which allready did before installing sane-backend)

$ scanimage -L
says no scanner found. when i check with it says one scanner found in usb.

found USB scanner (vendor=0x03f0, product=0x1405, chip=GL646_HP?) at libusb:005:004

but still can't scan. any ideas?

Ubuntu 10.04
kernel: 2.6.32-25-generic

---

### Post by novateando on 2011-02-10
I did all the steps before but I get this:

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

---

### Post by desertdog on 2011-06-14
try:
$sudo scanimage -L
If it works as sudo, but not as regular user, you have a permissions issue. See: [https://help.ubuntu.com/community/SettingScannerPermissions](https://help.ubuntu.com/community/SettingScannerPermissions)

---

### Post by idechix on 2011-10-17
Hi All!

My Scanjet 3670 worked fine when I was on Ubuntu 11.04, but with Ubuntu 11.10 it doesn't work anymore.

It is really weird because sane seems to be exactly the same in Ubuntu 11.04 and 11.10...

I can see the scanner with **sane-find-scanner**, but **scanimage -L** always says "No scanners were identified.".

In debug mode I get this :
> 
[sanei_debug] Setting debug level of genesys to 255.
[genesys] SANE Genesys backend version 1.0 build 63 from sane-backends 1.0.22
[genesys] SANE Genesys backend built with libusb
[genesys] sane_init: authorize != null
[genesys] sane_init: little endian machine
[genesys] probe_genesys_devices: start
[genesys] attach: start: devp != NULL, may_wait = 0
[genesys] attach: trying to open device `libusb:004:006'
**[genesys] attach: couldn't open device `libusb:004:006': Invalid argument**
[genesys] probe_genesys_devices: exit
[genesys] sane_init: exit
[genesys] sane_get_devices: start: local_only = false
[genesys] probe_genesys_devices: start
[genesys] attach: start: devp != NULL, may_wait = 0
[genesys] attach: trying to open device `libusb:004:006'
[genesys] attach: couldn't open device `libusb:004:006': Invalid argument
[genesys] probe_genesys_devices: exit
[genesys] sane_get_devices: exit
[genesys] sane_exit: start
[genesys] sane_exit: exit


I tried to compile the latest sane from GIT, with libusb 0.1 and then with libusb 1.0 but it was always the same behavior.

Any ideas?

---

### Post by htmue on 2011-10-31
Hi!

I'm having the same issue, the Scanjet 3670 worked plug-and-play without any problems on 11.04 but doesn't work after upgrade to 11.10.

**sane-find-scanner** finds the scanner, but **scanimage -L** reports **Invalid argument** after trying to open the libusb device.

Is there a way to see the argument(s) that are invalid? Which arguments would be valid? Which component sends the invalid argument?

---

### Post by abhi.datt on 2012-02-07
Hi,
Could anyone make some progress on this issue. 

I found out that the drivers respnsible for this scanner is
sane-genesys
which is provided in 11.10 by package name:
libsane
The configuration file responnsible for this is in: 
/etc/sane.d/genesys.conf

And I could find the correct entry and identifier in this file

```
# Hewlett Packard ScanJet 3670c/3690c
usb 0x03f0 0x1405
```

But still Simple Scan or scanimage -L
does not find this scanner.

---

