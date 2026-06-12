---
title: "Gnomish problems (I think) when plugging in a camera"
date: 2010-01-25
forum: Desktop Environments
---

### Post by honestguvnor on 2010-01-25
When I plug in my digital camera to the USB port I see:

(1) A small popup window stating:
Unable to mount KODAK EasyShare P880 Zoom Digital Camera
Error initializing camera: -60: Could not lock the device

(2) 2 popups asking me what I want to do. The default is opening F-Spot

(3) 2 desktop icons which when clicked show the locations:
gphoto2://[usb:002,008]/store_00020001
gphoto2://[usb:002,008]/store_00010001
The first contains a couple of files which do not seem to mean much and the second a directory containing my photos which can be viewed and copied without problem (i.e. the important stuff works).

Unfortunately, when I try to subsequently run f-spot, gthumb, digikam and the like they freeze when trying to import and have to be force quit. Unmounting the files first makes no difference.

However, if I "killall gvfs-gphoto2-volume-monitor" (a suggestion posted elsewhere on the forum) and then plug in the camera, f-spot, digikam, gthumb and the like will successfully view and import the files in the camera (i.e. everything now works as it should).

Any suggestion on how to fix the behaviour of gnome (assuming the problem lies here)?

---

