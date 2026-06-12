---
title: "canon powershot A510 and digikam, libgphoto2"
date: 2005-05-28
forum: Desktop Environments
---

### Post by F for Fragging on 2005-05-28
Ok, I have a Canon Powershot A510. The first time I connected it to my PC and pressed "auto detect" in the "add camera" in digikam, it would detect a "USB PTP Class Camera" (because the A510 isn't in the camera list of libgphoto2 version 2.1.5). Even though it detected the A510 as a USB PTP class cam it worked fine, except for deleting, which I had to do with the cam myself. Digikam could connect to the cam and download the pictures from it.
However, since a week or so it hasn't been working very well. Digikam would complain that it couldn't connect to the cam anymore (even though it was turned on and connected properly), and I got it to work after a combination of re-inserting the usb cable in the camera and in another usb port on my mobo, turning the cam on and off. Today it did this as well, it said it couldn't connect to the cam. I tried turning the cam on/off again and unplug the usb cable and plug it in again, but it didn't work. Then I tried removing the cam from the "Add Camera" dialog and pressing "auto detect" again. After that it was working again, digikam could connect to the cam again.
I thought it could be a hardware problem with the cam because digikam sometimes had trouble connecting to it, but when I tried it in Windows XP (I have a dualboot with WXP) it worked fine, so it's not the cam.

So, in the beginning my cam was working fine in digikam and now it isn't always working because I have to pull all kinds of tricks to get it to work, as I described. That's strange, but I think that upgrading to a new release of libgphoto2 will fix it - [http://www.livejournal.com/users/hisham/13172.html](http://www.livejournal.com/users/hisham/13172.html) - so I checked the download page - [http://sourceforge.net/project/showfiles.php?group_id=8874&release_id=290239](http://sourceforge.net/project/showfiles.php?group_id=8874&release_id=290239) - on sourceforge. Version 2.1.6-rc1 can be found there. I downloaded 2.1.6-rc1and did the usual stuff,  extract and run sudo ./configure the configure-process went fine until the end:



Configuration (libgphoto2_port)

        Source code location:    .
        Compiler:                gcc

        SERIAL support:          yes

        Locking mechanism (for serial ports):
        Use resmgr:              no
        Use baudboy:             no
        Use ttylock:             no
        Use lockdev:             no

        USB support:             no (required for USB cameras, [http://sourceforg](http://sourceforg)
e.net/projects/libusb/)

        Build API documentation: no (not requested)
        Use ltdl.h:              no



Configuration (libgphoto2):

        Source code location:      .
        Version:                   2.1.6rc1
        Compiler:                  gcc

        Build API documentation:   no (not requested)
        pkg-config:                no ([http://www.freedesktop.org/software/pkgco](http://www.freedesktop.org/software/pkgco)                                                                          nfig)
        EXIF support:              no ([http://www.sourceforge.net/projects/libex](http://www.sourceforge.net/projects/libex)                                                                            if)
        JPEG mangling support:     yes
        Use ltdl.h:                no
        /proc/meminfo:             available



Please check whether the configuration I detected matches what you
would like to have. E.g. make sure that USB support is there if you
intend to use USB cameras with libgphoto2.

Please also check that PKG_CONFIG_PATH contains ${libdir}/pkgconfig
before compiling any libgphoto2 frontend.

sander@boven:~/libgphoto2-2.1.6rc1$



So my question is, why doesn't it want to compile with USB support? Version 2.1.5 of libgphoto2 which is currently installed does work with my USB cam. Can anyone please tell me how to compile with USB support, or does anyone know if there is a DEB of 2.1.6-rc1 somewhere?

---

### Post by F for Fragging on 2005-05-30
Ok, someone told me to install the development libraries for libusb and libexif. I installed them via the APT repo, and after that the configure script detected them and it would compile with USB and EXIF support. Then I did sudo make and sudo make install and everything compiled and installed fine.

But one problem remains... the list of camera's which can be seen in in the KDE Control Center under Peripherals -> Digital Camera -> Add has not been updated after I installed version 2.1.6rc1 of libgphoto2... What can I do to fix this?

---

### Post by skyboy on 2005-05-31
I got same problem with my panasonic cam, and fixed the problem (every time) in digiKam by removing the previously "auto-detected" cam and auto detecting again.  At least, I dont have to trick with the cable but sure it is still not a clean fix.

---

### Post by F for Fragging on 2005-05-31
Yes, I discovered that was the solution for me as well. If it couldn't connect to my A510 anymore I had to delete the "USB PTP Class camera" and autodetect it again, which would give me the same "USB PTP Class camera" again. Then it would work.

But have you also tried compiling a newer version of libgphoto2?

---

### Post by skyboy on 2005-05-31
no, I havent yet but I could give it a try later on.

---

