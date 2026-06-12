---
title: "skype, video  crashes whole program"
date: 2009-05-18
forum: General Help
---

### Post by c/Kr3t on 2009-05-18
whenever i try to start my own video feed, it just crashes skype all together.

i tried looking for threads to help but none showed up.

i'm using a logitech quickcam (usb) and on [https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams) say in the non-working cameras  --  Logitech Quickam Web (USB)  --   , it's listed but is that the same as mine?  is there any way to tell what kind i have compared to the list?

---

### Post by c/Kr3t on 2009-05-19
i just tried the walkthrough from [http://ubuntuforums.org/showthread.php?p=3856516#post3856516/](http://ubuntuforums.org/showthread.php?p=3856516#post3856516/) and this is what i get after
```
gstfakevideo v4lsrc device=/dev/video1 ! ffmpegcolorspace
```
```
gst.c create_pipeline (155): pipeline created
gst.c create_pipeline (159): pipeline linked
gst.c shim_ioctl (201): request=80685600 nr 0
gst.c shim_ioctl (313): result=-1 error=515 Unknown error 515

gst.c shim_ioctl (201): request=803c7601 nr 1
gst.c shim_ioctl (208): VIDIOCGCAP
gst.c shim_ioctl (313): result=0 error=0 Success

gst.c bus_callback (105): Error: Could not get/set settings from/on resource.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL hdmi
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL hdmi
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL hdmi
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
gst.c shim_ioctl (201): request=80685600 nr 0
gst.c shim_ioctl (313): result=-1 error=515 Unknown error 515

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

Starting the process...
gst.c bus_callback (105): Error: Could not get/set settings from/on resource.
Skype Xv: Xv ports available: 32
Skype XShm: XShm support enabled
Skype Xv: Using Xv port 280
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL hdmi
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL hdmi
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL hdmi
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL hdmi
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL hdmi
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL hdmi
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL hdmi
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL hdmi
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL hdmi
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
Skype Xv: Xv ports available: 31
Skype XShm: XShm support enabled
Skype Xv: Using Xv port 281

```

---

