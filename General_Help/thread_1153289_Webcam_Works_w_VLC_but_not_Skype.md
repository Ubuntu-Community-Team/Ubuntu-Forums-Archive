---
title: "Webcam Works w/ VLC but not Skype"
date: 2009-05-08
forum: General Help
---

### Post by zzzBrett on 2009-05-08
I've followed the documentation on how to get my webcam working.  According to [https://wiki.ubuntu.com/SkypeWebCams]("https://wiki.ubuntu.com/SkypeWebCams"), my Logitech Quickcam 3000 for Business (a UVC Video cam) should work "out of the box" with the latest version of Skype.  I use Ubuntu 9.04 x64.

I can see that the webcam is mounted at /dev/video1, and with that information, I can capture the video device using VLC and it is fine quality.  When I try to select the webcam using Skype, all I get is a green video box.

Any ideas on what could be wrong? I was thinking it may have something to do with me using a 64 bit distro, but it seems like if it works with VLC, it should work with skype.

Thanks,
Brett

---

### Post by Bindsa on 2009-05-08
If your using Jaunty you're probably suffering from a bug, follow the workaround described here:
[http://ubuntuforums.org/showthread.php?t=1145967](http://ubuntuforums.org/showthread.php?t=1145967)

---

### Post by zzzBrett on 2009-05-08
> **Bindsa said:**
> If your using Jaunty you're probably suffering from a bug, follow the workaround described here:
[http://ubuntuforums.org/showthread.php?t=1145967](http://ubuntuforums.org/showthread.php?t=1145967)

If you're referring to the bug "Camera doesn't mount when connected and switched on", I don't think thats my problem.  It is referring to a mounted digital camera it seems.

---

### Post by spiderbatdad on 2009-05-08
try this in your terminal, if it works you can edit the launcher command:
```
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype

or
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

```

---

### Post by zzzBrett on 2009-05-10
I fixed the problem by reinstalling UVC with the latest release, then with a modprobe for the webcam.

Thanks for the suggestions.

---

