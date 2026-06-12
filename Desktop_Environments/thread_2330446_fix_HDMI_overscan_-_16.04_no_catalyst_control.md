---
title: "fix HDMI overscan - 16.04 no catalyst control"
date: 2016-07-11
forum: Desktop Environments
---

### Post by Ubbly on 2016-07-11
How to fix HDMI overscan ? Desktop is spilling over screen edges.

After install I find out 16.04 LTS cannot have catalyst control centre any more. I always used that to fix my overscan.
The monitor does not have an overscan option.

GPU Radeon HD5850
Monitor Viewsonic HD 1080p

I'd like to keep using the radeon card with the open source drivers but don't know how to fix overscan issue.

Something with xrandr ?

---

### Post by Ubbly on 2016-07-13
...really - nobody else has this issue - with all the thousands of radeon users out there ? Got to say I'm surprised that AMD were just dumped like this.

---

### Post by wildmanne39 on 2016-07-13
Please be patient the forum has been down a lot in the last few days.

---

### Post by grahammechanical on 2016-07-13
> Got to say I'm surprised that AMD were just dumped like this.

Actually, It is AMD that decided not to provide a proprietary video driver for Ubuntu 16.04 because 16.04 uses a version of the X server that their proprietary drivers do not support. And they did not want to do the work to provide support. Their development effort was going in a different direction. Ubuntu developers had no choice but to not put AMD proprietary drivers in 16.04.

[https://tjaalton.wordpress.com/2016/03/11/no-catalystfglrx-video-driver-in-ubuntu-16-04/](https://tjaalton.wordpress.com/2016/03/11/no-catalystfglrx-video-driver-in-ubuntu-16-04/)
> 
The fglrx driver is now deprecated in 16.04, and we  recommend its open source alternatives (radeon and amdgpu). AMD put a  lot of work into the drivers, and we backported kernel code from Linux  4.5 to provide a better experience. 


When  upgrading to Ubuntu 16.04 from a previous release, both the fglrx  driver and the xorg.conf will be removed, so that the system is set to  use either the amdgpu driver or the radeon driver (depending on the  available hardware).

[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes)

Things may improve when you upgrade to 16.04.1 when it is released in a few weeks as AMD were intending to be giving better open source driver support by the summer of this year.

Oh, by the way, I have been trying for more than a day to post a reply to your post but the problems to the forums prevented me. There is not much a person can do when the response to "Post Quick Reply" is a page saying that the forum is down. Whereas, you were able to use a brief period when things were fixed to make your second post but a short while after that the problems began again.

Regards

---

### Post by Ubbly on 2016-07-14
Yes apologies for my impatience and thanks for the answers. So i will wait for further updates. But isn't there an xrandr fix ?

---

### Post by shivamg95 on 2016-09-13
> **Ubbly said:**
> How to fix HDMI overscan ? Desktop is spilling over screen edges.

After install I find out 16.04 LTS cannot have catalyst control centre any more. I always used that to fix my overscan.
The monitor does not have an overscan option.

GPU Radeon HD5850
Monitor Viewsonic HD 1080p

I'd like to keep using the radeon card with the open source drivers but don't know how to fix overscan issue.

Something with xrandr ?

I am also suffering with the exact problem. And unable to find any solution yet. If you find any, please reply here.

---

### Post by chayzer on 2016-09-15
xrandr --output HDMI-0 --set underscan on

---

### Post by jonb876 on 2017-02-15
I hope you fixed it, but the above solutions didnt work very well for me, so I had to hunt for better ones. Just so other people finding this have the solution that worked for me, here it is:

xrandr - q  #find out which screen it is (mine was DVI-0)
xrandr --output DVI-0 --set underscan on  #add your screen as output
xrandr --output DVI-0 --set "underscan hborder" 60 --set "underscan vborder" 30 #change those numbers til its right

---

### Post by moritz-schappler on 2017-04-08
Thanks. Worked for me, too (Ubuntu 16.04, Kernel 4.7, AMD A6-6400K/Radeon HD 8470D) .
To make this permanent on startup, even with different window managers (Kodi-Standalone, Lightdm), you could use a settings file [FONT=courier new]/etc/X11/Xsession.d/45custom_xrandr-settings[/FONT] containing the last two xrandr commands. [[Taken from this post]]("http://unix.stackexchange.com/a/125613/224975").

---

### Post by johannezzz on 2018-02-11
This xrandr thing work for me, but i did this custom xrandr file and copy it to [COLOR=#000000][FONT=courier new]/etc/X11/Xsession.d/45custom_xrandr-settingsit [/FONT][/COLOR] its not do anything... sorry my (non native) english. ubuntu 18.04

---

### Post by QIII on 2018-02-11
Please do not wake such old threads.  You are welcome to start a new thread linking back to this thread.

Closed.

---

