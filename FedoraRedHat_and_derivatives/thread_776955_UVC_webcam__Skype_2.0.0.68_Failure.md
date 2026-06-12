---
title: "UVC webcam / Skype 2.0.0.68 Failure"
date: 2008-05-01
forum: Fedora/RedHat and derivatives
---

### Post by Peacepunk on 2008-05-01
Gstreamer & gstreamer-devel installed. gstfakevideo installed; **Fedora 7** and Skype 2.0.0.68

-- As such, skype still reports lots of errors & no video is available;
-- **luvcview works fine**
-- Skype detects both devices, the gstfake on /video0, and the M678 on /video1.

-- This tested with both **i810** and **intel **modsetting drivers
-- This tested **without** Compiz

None works.

_some outputs:_
**dmseg|tail** *-relevant part only*
usb 2-1: new full speed USB device using uhci_hcd and address 11
usb 2-1: configuration #1 chosen from 1 choice
uvcvideo: Found UVC 1.00 device M678  (0e8d:0004)
uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
input: M678  as /class/input/input17

*Note: warning "Failed to query..." deemed non-threateninig by UVC driver devs*
```

**lsusb***-relevant part only*
Bus 002 Device 011: ID 0e8d:0004 

```
```
**lsmod|grep uvcvideo**
videodev               28097  1 uvcvideo
v4l1_compat            15813  2 uvcvideo,videodev
v4l2_common            18625  2 uvcvideo,videodev

```
[i]
/dev/video0[/i] mv'ed to */dev/video1*

Skype set to use [i]/dev/video0
[/i]
[b]
cli used:[/b]
.```
/gstfakevideo v4lsrc device=/dev/video0 ! videoscale ! ffmpegcolorspace

```

**output from terminal:**
```
gst.c create_pipeline (155): pipeline created
gst.c create_pipeline (159): pipeline linked
gst.c shim_ioctl (201): request=803c7601 nr 1
gst.c shim_ioctl (208): VIDIOCGCAP
gst.c shim_ioctl (313): result=0 error=0 Success

gst.c shim_ioctl (201): request=80207609 nr 9
gst.c shim_ioctl (255): VIDIOCGWIN
gst.c shim_ioctl (313): result=0 error=0 Success

gst.c shim_ioctl (201): request=c0307602 nr 2
gst.c shim_ioctl (214): VIDIOCGCHAN
gst.c shim_ioctl (313): result=0 error=0 Success

gst.c shim_ioctl (201): request=40307603 nr 3
gst.c shim_ioctl (219): VIDIOCSCHAN
gst.c shim_ioctl (313): result=0 error=0 Success

gst.c shim_ioctl (201): request=c0307602 nr 2
gst.c shim_ioctl (214): VIDIOCGCHAN
gst.c shim_ioctl (313): result=0 error=0 Success

gst.c shim_ioctl (201): request=80887614 nr 20
gst.c shim_ioctl (313): result=-1 **error=22 Invalid argument**

gst.c shim_ioctl (201): request=80887614 nr 20
gst.c shim_ioctl (313): result=-1 **error=22 Invalid argument**

gst.c shim_ioctl (201): request=80887614 nr 20
gst.c shim_ioctl (313): result=-1 [b]error=22 Invalid argument
[/b]
gst.c shim_ioctl (201): request=80887614 nr 20
gst.c shim_ioctl (313): result=-1 [b]error=22 Invalid argument
[/b]
gst.c shim_ioctl (201): request=80887614 nr 20
gst.c shim_ioctl (313): result=-1 [b]error=22 Invalid argument
[/b]
gst.c shim_ioctl (201): request=80887614 nr 20
gst.c shim_ioctl (313): result=-1 error=22 Invalid argument

gst.c shim_ioctl (201): request=80887614 nr 20
gst.c shim_ioctl (313): result=-1 [b]error=22 Invalid argument
[/b]
gst.c shim_ioctl (201): request=80887614 nr 20
gst.c shim_ioctl (313): result=-1[b] error=22 Invalid argument
[/b]
gst.c shim_ioctl (201): request=80887614 nr 20
gst.c shim_ioctl (313): result=-1 [b]error=22 Invalid argument
[/b]
gst.c shim_ioctl (201): request=80887614 nr 20
gst.c shim_ioctl (313): result=-1 [b]error=22 Invalid argument
[/b]
gst.c shim_ioctl (201): request=80887614 nr 20
gst.c shim_ioctl (313): result=-1 [b]error=22 Invalid argument
[/b]
[b]gst.c shim_ioctl (201): request=80685600 nr 0
gst.c shim_ioctl (313): result=-1 _error=515 Unknown error 515_
[/b]
gst.c shim_ioctl (201): request=803c7601 nr 1
gst.c shim_ioctl (208): VIDIOCGCAP
gst.c shim_ioctl (313): result=0 error=0 Success
[b]
gst.c bus_callback (105): Error: Could not read from resource.
gst.c bus_callback (105): Error: Could not read from resource.
gst.c bus_callback (105): Error: Could not read from resource.
gst.c bus_callback (105): Error: Could not read from resource.
gst.c bus_callback (105): Error: Could not read from resource.
gst.c bus_callback (105): Error: Could not read from resource.
gst.c bus_callback (105): Error: Could not read from resource.
gst.c bus_callback (105): Error: Could not read from resource.
gst.c bus_callback (105): Error: Could not read from resource.
gst.c bus_callback (105): Error: Could not read from resource.
gst.c bus_callback (105): Error: Could not read from resource.
*gst.c bus_callback (105): Error: Could not negotiate format*[/b]
gst.c shim_ioctl (201): request=803c7601 nr 1
gst.c shim_ioctl (208): VIDIOCGCAP
gst.c shim_ioctl (313): result=0 error=0 Success

gst.c shim_ioctl (201): request=80207609 nr 9
gst.c shim_ioctl (255): VIDIOCGWIN
gst.c shim_ioctl (313): result=0 error=0 Success

gst.c shim_ioctl (201): request=c0307602 nr 2
gst.c shim_ioctl (214): VIDIOCGCHAN
gst.c shim_ioctl (313): result=0 error=0 Success

gst.c shim_ioctl (201): request=40307603 nr 3
gst.c shim_ioctl (219): VIDIOCSCHAN
gst.c shim_ioctl (313): result=0 error=0 Success

gst.c shim_ioctl (201): request=c0307602 nr 2
gst.c shim_ioctl (214): VIDIOCGCHAN
gst.c shim_ioctl (313): result=0 error=0 Success

gst.c shim_ioctl (201): request=80887614 nr 20
gst.c shim_ioctl (313): result=-1 **error=22 Invalid argument**

gst.c shim_ioctl (201): request=80887614 nr 20
gst.c shim_ioctl (313): result=-1 **error=22 Invalid argument**

gst.c shim_ioctl (201): request=80887614 nr 20
gst.c shim_ioctl (313): result=-1 [b]error=22 Invalid argument
[/b]
gst.c shim_ioctl (201): request=80887614 nr 20
gst.c shim_ioctl (313): result=-1 **error=22 Invalid argument**

gst.c shim_ioctl (201): request=80887614 nr 20
gst.c shim_ioctl (313): result=-1 e[b]rror=22 Invalid argument
[/b]
gst.c shim_ioctl (201): request=80887614 nr 20
gst.c shim_ioctl (313): result=-1 [b]error=22 Invalid argument
[/b]
gst.c shim_ioctl (201): request=80887614 nr 20
gst.c shim_ioctl (313): result=-1 **error=22 Invalid argument**

gst.c shim_ioctl (201): request=80887614 nr 20
gst.c shim_ioctl (313): result=-1 [b]error=22 Invalid argument
[/b]
gst.c shim_ioctl (201): request=80887614 nr 20
gst.c shim_ioctl (313): result=-1 **error=22 Invalid argument**

gst.c shim_ioctl (201): request=80887614 nr 20
gst.c shim_ioctl (313): result=-1 **error=22 Invalid argument**

gst.c shim_ioctl (201): request=80887614 nr 20
gst.c shim_ioctl (313): result=-1 **error=22 Invalid argument**
[b]
gst.c bus_callback (105): Error: Could not read from resource.
gst.c bus_callback (105): Error: Could not read from resource.
gst.c bus_callback (105): Error: Could not read from resource.
gst.c bus_callback (105): Error: Could not read from resource.
gst.c bus_callback (105): Error: Could not read from resource.
gst.c bus_callback (105): Error: Could not read from resource.
gst.c bus_callback (105): Error: Could not read from resource.
gst.c bus_callback (105): Error: Could not read from resource.
gst.c bus_callback (105): Error: Could not read from resource.
gst.c bus_callback (105): Error: Could not read from resource.
gst.c bus_callback (105): Error: Could not read from resource.
gst.c bus_callback (105): Error: Could not negotiate format
gst.c shim_ioctl (201): request=80685600 nr 0
gst.c shim_ioctl (313): result=-1 _error=515 Unknown error 515_[/b]

gst.c shim_ioctl (201): request=803c7601 nr 1
gst.c shim_ioctl (208): VIDIOCGCAP
gst.c shim_ioctl (313): result=0 error=0 Success

gst.c shim_ioctl (201): request=800e7606 nr 6
gst.c shim_ioctl (236): VIDIOCGPICT
gst.c shim_ioctl (313): result=0 error=0 Success

gst.c shim_ioctl (201): request=400e7607 nr 7
gst.c shim_ioctl (243): VIDIOCSPICT depth:24, colorspace:15
gst.c shim_ioctl (313): result=0 error=0 Success

gst.c shim_ioctl (201): request=80207609 nr 9
gst.c shim_ioctl (255): VIDIOCGWIN
gst.c shim_ioctl (313): result=0 error=0 Success

gst.c shim_ioctl (201): request=4020760a nr 10
gst.c shim_ioctl (259): VIDIOCSWIN
gst.c shim_ioctl (313): result=0 error=0 Success

gst.c shim_ioctl (201): request=803c7601 nr 1
gst.c shim_ioctl (208): VIDIOCGCAP
gst.c shim_ioctl (313): result=0 error=0 Success

gst.c shim_ioctl (201): request=80207609 nr 9
gst.c shim_ioctl (255): VIDIOCGWIN
gst.c shim_ioctl (313): result=0 error=0 Success

gst.c shim_ioctl (201): request=c0307602 nr 2
gst.c shim_ioctl (214): VIDIOCGCHAN
gst.c shim_ioctl (313): result=0 error=0 Success

gst.c shim_ioctl (201): request=40307603 nr 3
gst.c shim_ioctl (219): VIDIOCSCHAN
gst.c shim_ioctl (313): result=0 error=0 Success

gst.c shim_ioctl (201): request=c0307602 nr 2
gst.c shim_ioctl (214): VIDIOCGCHAN
gst.c shim_ioctl (313): result=0 error=0 Success

gst.c shim_ioctl (201): request=80887614 nr 20
gst.c shim_ioctl (313): result=-1 [b]error=22 Invalid argument
[/b]
gst.c bus_callback (105): Error: Could not read from resource.
gst.c shim_ioctl (201): request=80887614 nr 20
gst.c shim_ioctl (313): result=-1 [b]error=22 Invalid argument
[/b]
gst.c bus_callback (105): Error: Could not read from resource.
gst.c shim_ioctl (201): request=80887614 nr 20
gst.c shim_ioctl (313): result=-1 [b]error=22 Invalid argument
[/b]
gst.c bus_callback (105): Error: Could not read from resource.
gst.c shim_ioctl (201): request=80887614 nr 20
gst.c shim_ioctl (313): result=-1 **error=22 Invalid argument**

gst.c bus_callback (105): Error: Could not read from resource.
gst.c shim_ioctl (201): request=80887614 nr 20
gst.c shim_ioctl (313): result=-1 **error=22 Invalid argument**

gst.c bus_callback (105): Error: Could not read from resource.
gst.c shim_ioctl (201): request=80887614 nr 20
gst.c shim_ioctl (313): result=-1 e**rror=22 Invalid argument**

gst.c bus_callback (105): Error: Could not read from resource.
gst.c shim_ioctl (201): request=80887614 nr 20
gst.c shim_ioctl (313): result=-1 e**rror=22 Invalid argument**

gst.c bus_callback (105): Error: Could not read from resource.
gst.c shim_ioctl (201): request=80887614 nr 20
gst.c shim_ioctl (313): result=-1 [b]error=22 Invalid argument
[/b]
gst.c bus_callback (105): Error: Could not read from resource.
gst.c shim_ioctl (201): request=80887614 nr 20
gst.c shim_ioctl (313): result=-1 [b]error=22 Invalid argument
[/b]
gst.c bus_callback (105): Error: Could not read from resource.
gst.c shim_ioctl (201): request=80887614 nr 20
gst.c shim_ioctl (313): result=-1 **error=22 Invalid argument**

gst.c bus_callback (105): Error: Could not read from resource.
gst.c shim_ioctl (201): request=80887614 nr 20
gst.c shim_ioctl (313): result=-1 **error=22 Invalid argument**

gst.c bus_callback (105): Error: Could not read from resource.
gst.c bus_callback (105): Error: Could not negotiate format
gst.c shim_ioctl (201): request=80685600 nr 0
gst.c shim_ioctl (313): result=-1_** error=515 Unknown error 515**_

gst.c shim_ioctl (201): request=803c7601 nr 1
gst.c shim_ioctl (208): VIDIOCGCAP
gst.c shim_ioctl (313): result=0 error=0 Success

gst.c shim_ioctl (201): request=800e7606 nr 6
gst.c shim_ioctl (236): VIDIOCGPICT
gst.c shim_ioctl (313): result=0 error=0 Success

gst.c shim_ioctl (201): request=400e7607 nr 7
gst.c shim_ioctl (243): VIDIOCSPICT depth:24, colorspace:15
gst.c shim_ioctl (313): result=0 error=0 Success

gst.c shim_ioctl (201): request=80207609 nr 9
gst.c shim_ioctl (255): VIDIOCGWIN
gst.c shim_ioctl (313): result=0 error=0 Success

gst.c shim_ioctl (201): request=4020760a nr 10
gst.c shim_ioctl (259): VIDIOCSWIN
gst.c shim_ioctl (313): result=0 error=0 Success
[b]
Starting the process...
Skype Xv: Xv ports available: 1
Skype XShm: XShm support enabled
Skype Xv: Using Xv port 73
[/b]
```

I did my homework... Can't find how to get this thng to hook to Ekiga as well by the way. All parameters from gstreamer-properties tested too.
[size="3"]?? Any Ideas ??[/size]

---

