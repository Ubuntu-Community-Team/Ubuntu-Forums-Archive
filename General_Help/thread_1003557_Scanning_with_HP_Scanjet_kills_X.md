---
title: "Scanning with HP Scanjet kills X"
date: 2008-12-06
forum: General Help
---

### Post by markofealing on 2008-12-06
I'm running Kubuntu 8.10 (KDE4) and I'm having problems getting any scanning software to work without crashing X!

I've had the same experience on two different PCs (one 32-bit and the other 64-bit), both clean installs.

Sane is driving me insane! I've tried it with the following front-ends, all detect the HP ScanJet 7400C which is supported by sane using USB [http://www.sane-project.org/sane-mfgs.html#SCANNERS](http://www.sane-project.org/sane-mfgs.html#SCANNERS) :

gscan2pdf
xsane
skanlite (native KDE4 application)

Before I run any of the above apps I did a **sane-find-scanner** to make sure my scanner was detected. The following result was displayed:

[I]found USB scanner (vendor=0x03f0 [hp], product=0x0801 [hp scanjet 7400c]) at libusb:006:003                                                                     
found USB scanner (vendor=0x0547, product=0x0201) at libusb:003:002 [/I]   

doing a lsusb confirmed the scanner was detected:

*Bus 006 Device 003: ID 03f0:0801 Hewlett-Packard ScanJet 7400c*

Running skanlite (the others have the same effect but just crash X so are not very helpful).

[I]
Application: Skanlite (skanlite), signal SIGSEGV
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb61516c0 (LWP 5971)]
(no debugging symbols found)
[KCrash handler]
#6  0xb6a609b8 in ?? () from /lib/tls/i686/cmov/libc.so.6
#7  0xb6a62865 in malloc () from /lib/tls/i686/cmov/libc.so.6
#8  0xb6c07d47 in operator new () from /usr/lib/libstdc++.so.6
#9  0xb6ef195a in ?? () from /usr/lib/libQtGui.so.4
#10 0xb6ef20cd in ?? () from /usr/lib/libQtGui.so.4
#11 0xb6e1b1a7 in QImage::paintEngine () from /usr/lib/libQtGui.so.4
#12 0xb6e81e46 in QPainter::begin () from /usr/lib/libQtGui.so.4
#13 0xb6e84663 in QPainter::QPainter () from /usr/lib/libQtGui.so.4
#14 0xb6e26c12 in QImage::transformed () from /usr/lib/libQtGui.so.4
#15 0xb6e27a34 in QImage::scaledToWidth () from /usr/lib/libQtGui.so.4
#16 0xb754ced0 in ?? () from /usr/lib/libksane.so.0
#17 0xb754cfdb in ?? () from /usr/lib/libksane.so.0
#18 0xb7558129 in ?? () from /usr/lib/libksane.so.0
#19 0xb75626f1 in KSaneIface::KSaneWidget::scanPreview ()
   from /usr/lib/libksane.so.0
#20 0xb7562ae3 in KSaneIface::KSaneWidget::qt_metacall ()
   from /usr/lib/libksane.so.0
#21 0xb7940a60 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
#22 0xb7940e60 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
#23 0xb7365e61 in QAbstractButton::clicked () from /usr/lib/libQtGui.so.4
#24 0xb70b9199 in ?? () from /usr/lib/libQtGui.so.4
#25 0xb70bad94 in ?? () from /usr/lib/libQtGui.so.4
#26 0xb70bb026 in QAbstractButton::mouseReleaseEvent ()
   from /usr/lib/libQtGui.so.4
#27 0xb6dcf962 in QWidget::event () from /usr/lib/libQtGui.so.4
#28 0xb70b903e in QAbstractButton::event () from /usr/lib/libQtGui.so.4
#29 0xb715f910 in QPushButton::event () from /usr/lib/libQtGui.so.4
#30 0xb6d778ec in QApplicationPrivate::notify_helper ()
   from /usr/lib/libQtGui.so.4
#31 0xb6d800e1 in QApplication::notify () from /usr/lib/libQtGui.so.4
#32 0xb7dfa72d in KApplication::notify () from /usr/lib/libkdeui.so.5
#33 0xb792be61 in QCoreApplication::notifyInternal ()
   from /usr/lib/libQtCore.so.4
#34 0xb6d7f36e in QApplicationPrivate::sendMouseEvent ()
   from /usr/lib/libQtGui.so.4
#35 0xb6de9656 in ?? () from /usr/lib/libQtGui.so.4
#36 0xb6de89e5 in QApplication::x11ProcessEvent () from /usr/lib/libQtGui.so.4
#37 0xb6e127aa in ?? () from /usr/lib/libQtGui.so.4
#38 0xb65d66f8 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#39 0xb65d9da3 in ?? () from /usr/lib/libglib-2.0.so.0
#40 0xb65d9f61 in g_main_context_iteration () from /usr/lib/libglib-2.0.so.0
#41 0xb7956478 in QEventDispatcherGlib::processEvents ()
   from /usr/lib/libQtCore.so.4
#42 0xb6e11ea5 in ?? () from /usr/lib/libQtGui.so.4
#43 0xb792a52a in QEventLoop::processEvents () from /usr/lib/libQtCore.so.4
#44 0xb792a6ea in QEventLoop::exec () from /usr/lib/libQtCore.so.4
#45 0xb792cda5 in QCoreApplication::exec () from /usr/lib/libQtCore.so.4
#46 0xb6d77767 in QApplication::exec () from /usr/lib/libQtGui.so.4
#47 0x0804dbd7 in _start ()
#0  0xb7fc3430 in __kernel_vsyscall ()[/I]

The smilies in the above are nothing to do with me, just how this website translates character combinations1

If you then go to system log "ksystemlog" you get these error messages every 3 seconds (same result regardless of the front-end used):

[I]2008-12-06 13:19:13	athlonxp	kernel	[ 1421.040055] dvb-usb: recv bulk message failed: -75
2008-12-06 13:19:16	athlonxp	kernel	[ 1424.060171] dvb-usb: recv bulk message failed: -110[/I]

Restarting X does not clear this error, only a reboot sorts it out. 

Doing a lsusb and a sane-find-scanner still correctly displays the scanner attached!

[COLOR="Red"]**Anyone else experiencing this problem with KDE4 or Ubuntu generally?**[/COLOR]

I trying to fully move over from Windows XP, currently scanning is one of the major "show stoppers" so any help/ advice would be greatly appreciated.

When I rerun skanlite I get an error message 

BTW, both PCs are running the ATI proprietary drivers "No scanner device has been found."

Yet the scanner is still listed as before via terminal commands!

---

### Post by GregA on 2008-12-06
Sorry, I've removed my original reply as it didn't apply to your specific scanner (I run a multi-function printer scanner (HP OfficeJet 7310 which is 100% functional with Ubuntu - so I thought the HPLIP toolbox gui might be helpful for you also).

Now, it seems you may have to download and try several of the drivers from the Sane website that are close to the model you have.   Have you tried the Scanjet 4100C driver?)

---

### Post by markofealing on 2008-12-07
There is nothing quite like a "Live"! Cd to test linux so I've booted of the Kubuntu 7.10 CD, installed "build-essential" and xsane. The scanner appears in lsusb. I've not installed sane-utils so could not enter sane-find-scanner so was not expecting the scanner to work on firing up xsane.

Xsane found the scanner, so pressed SCAN and after a brief initialisation the scanner scanned my document. Unfortunately I'm not able to run gscan2pdf as this is not present in Kubuntu 7.10 and skanlite is KDE4 only but I have no reason to believe that they will not work.

Ksystem log is clear of any errors so I have fairly good reason to believe that this is a potential Kubuntu 8.10 bug.

I'll do some more testing, before I work out how to raise a bug report:

1. remove sane-utils from my 8.10 install
2. boot off the Ubuntu 8.10 Live! CD
3. boot off the Kubuntu 8.04 Live! CD (KDE3)

If any one else has any further testing suggestions then let me know. At this stage I don't think it is a scanner driver issue.

---

### Post by markofealing on 2008-12-07
Booted back to 8.10 and removed sane-utils, scanner still visible when doing a lsusb. Noticed that in removing sane-utils gscan2pdf was also uninstalled!

Ran xsane, which detected the scanner and on pressing SCAN it started to initialise it, after a minute it crashed!

Looking at the system log the following error was generated by kernal

[ 1698.576106] xsane[6165]: segfault at 43024228 ip b74869b8 sp bffa5dc4 error 6 in libc-2.8.90.so[b7415000+158000]

No idea what this means but unlike before none of the " kernel [ 1421.040055] dvb-usb: recv bulk message failed..." errors were generated and X did not crash.

I'll now see if I can get skanlite to work.

---

### Post by markofealing on 2008-12-07
No skanlite does not work (even after a reboot), it hangs and eventually I get a "device busy" error followed by "could not start ksmserver" followed by a Okay. On clicking Okay X reboots and I have to login again.

I'll try the other Live CDs to see when/ how this broke.

---

### Post by markofealing on 2008-12-14
I've now tried the Kubuntu 8.04.1 Live CD and the Ubuntu 8.10 Live CD.

As unsuccessful with Kubuntu 8.04 as with 8.10 and with Ubuntu 8.10 the scanner did at least try to initialise with xsane, but then xsane crashed followed by X Windows.

So is the answer to take the "retarded" approach and install Kubuntu 7.10? C

Currently more attractive proposition is to ditch Linux on my main PC all together and stick with Windows XP which has so far proved a 100% more reliable that Ubuntu (not just for scanning but also for dual display)?:mad:

---

### Post by markofealing on 2009-02-25
This problem has been reported as a bug in libsane!

See LaunchPad Bug reports #134754, 234841 and 221750. 

Solution appears to be in the latter bug which is to downgrade to libsane 1.0.17-1ubuntu4 (ex Dapper Drake) which can be found here:

[https://launchpad.net/ubuntu/dapper/hppa/libsane/1.0.17-1ubuntu4](https://launchpad.net/ubuntu/dapper/hppa/libsane/1.0.17-1ubuntu4)

Will test!

---

### Post by markofealing on 2009-03-28
> **markofealing said:**
> This problem has been reported as a bug in libsane!

See LaunchPad Bug reports #134754, 234841 and 221750. 

Solution appears to be in the latter bug which is to downgrade to libsane 1.0.17-1ubuntu4 (ex Dapper Drake) which can be found here:

[https://launchpad.net/ubuntu/dapper/hppa/libsane/1.0.17-1ubuntu4](https://launchpad.net/ubuntu/dapper/hppa/libsane/1.0.17-1ubuntu4)

Will test!

See [https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/234841](https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/234841) for details of the fix. 

Installing the following Debian packages upgrades XSANE to the latest version resolving the problem of X crashing. _**Downgrading is unnecessary.**_

[http://packages.debian.org/sid/update-inetd](http://packages.debian.org/sid/update-inetd)
[http://packages.debian.org/sid/sane-utils](http://packages.debian.org/sid/sane-utils)
[http://packages.debian.org/sid/libs/libsane-extras](http://packages.debian.org/sid/libs/libsane-extras) 
[http://packages.debian.org/sid/libsane](http://packages.debian.org/sid/libsane)

Lets hope Ubuntu 9.04 has the latest XSANE version installed by default.

PROBLEM RESOLVED

---

