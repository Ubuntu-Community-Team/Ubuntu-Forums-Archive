---
title: "Open Office Documents Not Printing"
date: 2009-01-06
forum: General Help
---

### Post by mikeman141 on 2009-01-06
Hey all,

This problem could be with so many places/things that I wasn't sure where to start, or even how to go about debugging.

I am hooked up over LAN to a Toshiba eStudio 850 priter/copier.  Printing from thunderbird/firefox/gedit works flawlessly.  Printing the test page from the printer setting in Ubuntu also works perfectly.  

Printing open office documents works with certain documents...but not all.  If I try and print just page 1, or just page 5, depending on the document, it will work.

The bug is repeatable, and consistent for a given document.  

The printing fails in the following way:

I click print, the menu comes up, the printing icon appears in the system tray, if I click on that to view it, it shows the document in queue, with "processing" written after it.  After the file disappears from there, a light on the printer blinks "print data" indicating it is recieving the data.  However, the job never appears in the job queue on the printer, and it never prints.

Can some one steer me in the right direction for how I can go about debugging?  Or a better forum?

Thanks

---

### Post by bryanl on 2009-01-06
I've had this problem with some documents printing to an HP5si. What I found I could do was to print to a pdf printer and then use Evince to print the pdf.

---

### Post by watersedge on 2009-01-20
I'm having a similar problem.  I've installed Hardy (8.04).  My printer is a Brother MFC8500.  It's on a print server.  I can print from every application I've tried...but none of the open office apps will print.  The printers are present and selected.  Everything looks fine...but when I hit 'print', nothing happens.  It does go to the queue, but immediately disappears as though it's being processed appropriately.  Everything seems to be fine...just no output.

I've tried uninstalling and reinstalling Open Office via the Add/Remove, but that didn't work.

I tried connecting the printer directly to the computer, but that didn't work (everything else printed okay, just not OpenOffice)

I can print the file to pdf, then print it from the pdf viewer, but I don't consider that a reasonable solution.

I'm running Ubuntu 8.04 with OpenOffice 2.3.

Any assistance or advice would be greatly appreciated.  Printing from my word processor is a must.

Thanks!

---

### Post by polmir on 2009-01-20
Try install:
```
sudo apt-get install cups-bsd
```

---

### Post by watersedge on 2009-01-20
Thanks for the reply.

I did sudo apt-get install cups-bsd

Here are the results:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package cups-bsd is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package cups-bsd has no installation candidate

I went to Synaptic Package Manager and reinstalled cups-bsd. It didn't help...everything still does the same thing, right down to the printer warming up and acting like it plans to print.

PLUS...I did the sudo apt-get install cups-bsd again and got the same results as the first time as noted above.

Any ideas?

Thanks a bunch for your help!

---

### Post by polmir on 2009-01-20
Send in the results of the commands:```
dpkg -l | grep cups
cat /etc/apt/sources.list
```

---

### Post by watersedge on 2009-01-20
jerry@sony-laptop:~$ dpkg -l | grep cups
ii  bluez-cups                                 3.26-0ubuntu6                     Bluetooth printer driver for CUPS
ii  cups-pdf                                   2.4.6-4ubuntu2                    PDF printer for CUPS
ii  cupsddk                                    1.2.0-0ubuntu1                    CUPS Driver Development Kit
ii  cupsddk-drivers                            1.2.0-0ubuntu1                    CUPS Driver Development Kit - Driver files
ii  cupswrappermfc8500                         1.0.2-1                           Brother MFC8500 CUPS wrapper driver
ii  cupsys                                     1.3.7-1ubuntu3.3                  Common UNIX Printing System(tm) - server
ii  cupsys-bsd                                 1.3.7-1ubuntu3.3                  Common UNIX Printing System(tm) - BSD comman
ii  cupsys-client                              1.3.7-1ubuntu3.3                  Common UNIX Printing System(tm) - client pro
ii  cupsys-common                              1.3.7-1ubuntu3.3                  Common UNIX Printing System(tm) - common fil
ii  cupsys-driver-gutenprint                   5.0.2-2ubuntu1                    printer drivers for CUPS
ii  hal-cups-utils                             0.6.13+svn86-0ubuntu4             CUPS integration with HAL
ii  libcupsimage2                              1.3.7-1ubuntu3.3                  Common UNIX Printing System(tm) - image libs
ii  libcupsys2                                 1.3.7-1ubuntu3.3                  Common UNIX Printing System(tm) - libs
ii  libgnomecups1.0-1                          0.2.3-1ubuntu1                    GNOME library for CUPS interaction
ii  python-cups                                1.9.34-0ubuntu1                   Python bindings for CUPS
jerry@sony-laptop:~$ 


jerry@sony-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) hardy main
jerry@sony-laptop:~$ 


Thanks!

---

### Post by polmir on 2009-01-21
Send in the results of the command:```
apt-cache search cups-dbg
```

---

### Post by watersedge on 2009-01-21
jerry@sony-laptop:~$ apt-cache search cups-dbg
jerry@sony-laptop:~$ 


It didn'nt provide any output on the screen.  Did I type it correctly?

---

