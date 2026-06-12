---
title: "dual screen working but freezing after cople of minutes"
date: 2013-07-10
forum: Desktop Environments
---

### Post by MPPP on 2013-07-10
Hi,

Just switched from win to Ubuntu 12.04.
I have a Nvidia NVS quadro 285 graphics card on my pc with two screens dual screen.
Upon installation ubuntu set the general driver, thus no Nvidia driver but the general defauld driver whereby only one, main screen works.

When in the additional driver application I set the driver to the second one (Nvidia propriety drivers where it says recommended) my two screens appear and work perfect. But after a while +- 6 min the ubuntu os completely freezes, becomes black or everything hangs, cant move mouse etc.

I can open the Nvidia settings panel and here everything seems to be recognized ok.
firts screen Dell, second Belinea, when I go to display settings in Ubuntu it gives first screen Dell, second rogtech.

Can you pls help me out in fixing this.
I think it might be a dual screen bug and I might need to install some bug files fixing this

Kind regards, Phil

---

### Post by mozkill on 2013-07-11
To me, this sounds like either bad system RAM or bad RAM on the video card.  Can you download memtest86 , boot from it, and then scan your memory and post a screenshot of your results?   Be aware that running this test takes 3+ hours in most cases.

---

### Post by MPPP on 2013-07-12
Hello mozkill, thank you very much for your reply !. I don't think it  has to do with bad ram on video card since the dual screens work perfect  on my win xp system.

**I found this on the ubuntu site but can't find the listed files since the links are broken.**

One of the features that ubuntu 12.04 promised was better support for  dual-monitor however after I upgraded from ubuntu 11.10  to ubuntu 12.04  I noticed if I change the display settings it will freeze for example I  noticed:

- I  move the external monitor to the left of laptop monitor , (or above it) it freezes
- I try to turn of the laptop monitor ,so I only have my external  monitor it will freeze again. the mouse and keyboard stop responding and  the only way key that respond is
 ALT+PRINTSCREEN+K (to restart the X server)

I openned a bug in [Launchpad]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/992778") and I tried every possible solution  after pulling my hair and not sleeping in the whole night .**Here is how I fixed it : **To fix dual monitor freeze in ubuntu 12.04 you need to install the older version of  *xserver-xorg-input-evdev*

1- Download the following two packages to your desktop:
[INDENT] - [xserver-xorg-input-evdev-udeb_2.6.99.901-1ubuntu3~lp921236_amd64.udeb]("https://launchpad.net/%7Esarvatt/+archive/sru1/+build/3118994/+files/xserver-xorg-input-evdev-udeb_2.6.99.901-1ubuntu3%7Elp921236_amd64.udeb") (24.0 KiB)[/INDENT] [INDENT] - [xserver-xorg-input-evdev_2.6.99.901-1ubuntu3~lp921236_amd64.deb]("https://launchpad.net/%7Esarvatt/+archive/sru1/+build/3118994/+files/xserver-xorg-input-evdev_2.6.99.901-1ubuntu3%7Elp921236_amd64.deb") (38.0 KiB)[/INDENT] 2- Open a terminal
[INDENT] cd Desktop[/INDENT] [INDENT] sudo dpkg -i *.deb[/INDENT] 3- Restart your computer or if you are lazy just restart the X Server (ALT+PRINTSCREEN +K)

maybe this would be a solution if I could find and run above mentionned files ? Could you help me out with this ?
Best regards,

---

