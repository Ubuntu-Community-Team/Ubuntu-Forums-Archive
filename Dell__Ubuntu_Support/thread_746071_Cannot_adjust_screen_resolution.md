---
title: "Cannot adjust screen resolution"
date: 2008-04-05
forum: Dell  Ubuntu Support
---

### Post by mikewave on 2008-04-05
My machine is a Dell Optiplex GX260 (P-IV) with 1GB of RAM. I have a dual-boot arrangement with Ubuntu (7.1/Gutsy Gibbon if memory serves) running the latest version of KDE in the Ubuntu repository, and MS Windows 2000 with the latest service packs. My display is a Samsung Syncmaster 730B.

The default resolution on my screen is too small for me to see. So I tried re-setting it to 1024 x 768. Unlike Windows or other Linux distros, there is no function in the control center to change screen resolution. So, I did what a fellow Ubuntu user did, and logged in as root under the "recovery" mode of Ubuntu (text user interface, X-windows off) and ran:

[COLOR="Red"]dpkg-reconfigure xserver-xorg[/COLOR]

I deselected the higher screen resolutions choosing only to leave 1024 x 768 and lower resolutions checked.

Long story short, my desktop is now permanently off-center (to the right) obscuring the system clock and about a fifth of the desktop. I tried several times to use my monitor's "auto adjust" function which works for Windows and other Linux distros. Didn't work. The screen right-sizes for a few seconds while the monitor is making the adjustment and then reverts the minute auto-adjustment is over.

My friend and fellow Linux user does not know how to address this problem.

Short of nuking my hard drive and reinstalling everything from scratch, how can I remedy this problem?

And BTW,* why* is there no easy way to adjust screen resolution in Ubuntu's version of KDE?

---

### Post by ridgeland on 2008-04-05
It could be the wrong driver for the video card.
It could just be settings in /etc/X11/xorg.conf
From the terminal try
$ gedit /etc/X11/xorg.conf
and have a look. 
If you want to make changes you have to use root.
$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.beforeIchangedit
always backup system files before editing them
$ sudo gedit /etc/X11/xorg.conf
Find your monitor's manual and look up horizontal and vertical refresh rates.  Does xorg.conf have the same range?
Here you can set the default resolution and which options show as available to the user.

---

### Post by nonewmsgs on 2008-04-18
in k menu there is "system settings" and then moniter and display.

it's almsot too powerful...it can allow things that make it reset to godawful resolutions next login.

---

### Post by jonathanmotes on 2008-04-18
If you run ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` from terminal it should automatically give you a configuration that works properly. Restart your computer for the changes to take affect.

UPDATE: I didn't see nonewmsgs's post. It is probably best to try it first.....

---

