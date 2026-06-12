---
title: "Herd 3 Testing (on Acer Aspire 9500)"
date: 2007-02-07
forum: Development CD/DVD Image Testing
---

### Post by munckfish on 2007-02-07
Hi

I've just managed to squeeze some time testing out the Herd 3 Live Cd on my laptop. I don't have any space to test out installing at the moment so I've just had to stick with the LiveCD. 

I'm really looking forward to upgrading when this comes out.

I posting here first as I need to dump the info I've collected, and I hope maybe some others will recognise some of the issues I've noted. I'll review and raise things on Launchpad in the coming days.

I've come across the following bugs:

**1. Add/Remove crash on login**

Maybe because of no network connection?

I get a crash report as the Live CD auto logs onto to the desktop.
   
Crash report contains:
	```
Script: /usr/sbin/update-app-install
	Package: gnome-app-install 0.3.11
	Traceback (Most recent call last)
	  File "/usr/sbin/update-app-install", line 17, in <module>
	    from AppInstall.CoreMenu import *
	ImportError: No module named AppInstall.CoreMenu

```
It looks a most like this bug  ...

- [https://bugs.launchpad.net/ubuntu/+source/gnome-app-install/+bug/83643](https://bugs.launchpad.net/ubuntu/+source/gnome-app-install/+bug/83643)

... but not quite as the stack track is different. Has anyone else had the same problem. It didn't happen for me everytime and I had a feeling it coincides with me booting without an active network connection. I'll need to check that out for certain tomorrow.


**2. Blank screen on boot**

Having an Acer 9500 with an ATI X700 I suffer from ...

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/22985](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/22985)

This is still a problem in Feisty Herd 3


**3. Caps Lock not working on TTY**

While resolving the problem in 2) I have to switch to a TTY and edit xorg.conf. While doing that I noticed that as well as it using the US keyboard layout on my UK keyboard it doesn't seem to recognise my CAPS-LOCK key.

I don't know enough to decide which package this is likely to be caused by. Can anyone make a suggestion there and I'll go about raising it in Launchpad, if it's not already there?


**4. Corrupt screen on changing screen resolution**

It seems Xorg correctly detects that my screen/card is capable of 1440x900 but when I try to change to this mode the desktop rendering is corrupt and unusable. Here's a screen shot:

[http://munckfish.net/tmp/feisty-xorg-screenres-corruption.jpg](http://munckfish.net/tmp/feisty-xorg-screenres-corruption.jpg)

I haven't had time to review the open issues here in detail and there seems to be a lot ...

[https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=screen+resolution+x700](https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=screen+resolution+x700)

I'll try to find time in my lunch hour to review them tomorrow.


**5. Webcam not supported**

Couldn't get it to work with my WebCam (LogiTech) I couldn't load the spca5xx driver with modprobe this driver seems to (somewhat) support my cam on Dapper. On the live Cd it appears to not be there, should I be surprised?


**6. The SD Card Reader doesn't work** 

I think that's this bug

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/62995](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/62995)


**7. Acer Hotkeys/Arcade keys not recognised**

Special 9500 Acer Hotkeys and Arcade keys don't work and don't even cause any kernel log messages in /var/log/kern.log.


**8. Volume control of bass speaker**

Sound seems to work brilliantly except the bass speaker is muted by default and once enabled it's volume isn't changed along with the main (Front) speakers when I change the PCI volume level. I need to research this a little more on LP.


That's all for now. ):P 

Cheers

---

