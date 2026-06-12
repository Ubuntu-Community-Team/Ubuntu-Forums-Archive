---
title: "XPS m1330: Will not fullscreen flv after update to 8.10 (intel video)"
date: 2009-01-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by pormogo on 2009-01-18
So it appears that after updating from 8.04 to 8.10 I can no longer full screen flash videos. This is a shame since just about everything else seems to have improved so much. Previously in 8.04 I was using a non packaged version of flash payer 10. figuring that was the issue I decided to remove it and install the restricted-extras package. Now everything I am using is "official"

[i]
ii  xserver-xorg-video-intel                   2:2.4.1-1ubuntu10                                    X.Org X server -- Intel i8xx, i9xx display d
ii  flashplugin-nonfree                        10.0.15.3ubuntu1~intrepid1                           Adobe Flash Player plugin installer
[/i]

From fire/swift fox about:plugins

[i]    File name: libflashplayer.so
    Shockwave Flash 10.0 r15[/i]

there is only one line. I am totally sure I purged the system of reference to the old libflashplayer.so plugin. 

On a side note I am using compiz.

any help would be most appreciated. While looking around I came across the following 8.10 bug. Can anyone here happen to confirm this? Is there a work around?

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/252094](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/252094)

---

