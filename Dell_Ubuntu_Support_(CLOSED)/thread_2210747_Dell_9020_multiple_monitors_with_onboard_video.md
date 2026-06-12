---
title: "Dell 9020 multiple monitors with onboard video"
date: 2014-03-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by baphomet2 on 2014-03-12
Hello,

I am using xubuntu 12.04.  For my job I'm having to develop a bootable image solution that works on a myriad of Dell workstations.  I have everything working except for the 9020.  I am limited to using 32-bit at the moment (have to support legacy), but have an option of moving to 64-bit in the future.  The only thing I can't get to work is the video (loaded the e1000e driver for the network interface).  I tried 64-bit so I could load the .deb packages from the Dell support site, but all that did was mirror my displays and there was no option to expand the desktop.  The system only saw one monitor connected to it, even though it was displaying the same desktop on all 3.  Under 32-bit it only shows/displays on one monitor and doesn't get anything else.  I'm using the onboard video (2 DisplayPort and 1 VGA) as the company did not want the optional Radeon card.

Here is the output of lspci so you can see the onboard video I am using:
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)

Does anyone know a driver/configuration I need to get it working under 32-bit?  If not how about 64?  I also tried getting the drivers directly from Intel, but it needs libglib >= 2.37.3 which I haven't been able to get installed on 12.04.

Thank you for your time.

---

### Post by baphomet2 on 2014-03-19
I'm guessing that I'm the only one messing with this kind of configuration.  Just in case someone else wants to do what I've been trying to do I figured I would post how I fixed it.

In order to get it to work I had to not only upgrade the kernel, but the xserver and libraries as well.  Here is the command for that:

sudo apt-get install linux-generic-lts-saucy xserver-xorg-lts-saucy libgl1-mesa-glx-lts-saucy

It has to be saucy as I tried raring and while it did display on 3 monitors it still only recognized it as a single display.

While that got the 3 monitors to display and be recognized as 3 separate monitors I was unable to configure them for desktop extension.  This is a major flaw with xubuntu as there is no native way to manipulate multiple displays.  I tried using arandr, but kept getting an error because the XRandR was upgraded to 1.4 and the python widgets need 1.2 or 1.3 to pass the version check.  This can be bypassed by running:

arandr --force-version

Everything works great after that and it still supports all the other models that I needed to support.

I hope that someone finds this useful.

---

