---
title: "Graphics on inspiron 1720"
date: 2007-11-27
forum: Dell  Ubuntu Support
---

### Post by philip2005 on 2007-11-27
I'm trying to test out ubuntu 64 bit on my 1720 using the live cd, but i can't get it to go to a resolution above 800x600. I've set the graphics driver to nvidea 8 series (which is what i have), and it automatically selects plug and play monitor. But if i try to select a diffeent monitor it asks me for the driver for it. Is there one on the cd?

---

### Post by lambros on 2007-11-29
> **philip2005 said:**
> I'm trying to test out ubuntu 64 bit on my 1720 using the live cd, but i can't get it to go to a resolution above 800x600. I've set the graphics driver to nvidea 8 series (which is what i have), and it automatically selects plug and play monitor. But if i try to select a diffeent monitor it asks me for the driver for it. Is there one on the cd?

I have a Dell Inspiron 1720 laptop, and I can confirm that Ubuntu 7.10 (gutsy), 64 bit, works fine on this system (after a little tweaking).

From what I remember, you get a better experience from the Live CD if you choose the "safe graphics" option on booting.  I think I managed to get the native 1440x900 screen resolution working that way.

In the installed system, you can use the Restricted Drivers Manager to install the nVidia driver for your card, and that works without a hitch.  The driver is not on the CD - you need to be connected to the Internet to fetch it.

Once you have the nVidia driver installed, it should be no problem to set your native screen resolution.

Problems I had:

Sadly, WiFi does not work out-of-the-box.  The Restricted Drivers Manager can easily fix that for you (but you'll need a wired connection to download the necessary drivers).

Sound also did not work.  To fix this, I enabled the "Backports" repository (in Synaptic Package Manager).  Then I installed the "linux-backports-modules-generic" package.  That got sound working after a reboot.

The Ubuntu bootup splash logo does not display at all.  The screen goes completely black (with the backlight off).  I haven't yet found a solution to this.  A bug-report has been filed:
[https://bugs.launchpad.net/bugs/150930](https://bugs.launchpad.net/bugs/150930)
but none of the workarounds are effective for me.  If this is annoying, you can disable the splash logo (post back if you want instructions).  I noticed an improvement in bootup speed after doing this.

[edit]
[COLOR="Red"]Very important[/COLOR] - my laptop suffered from excessive load/unload cycles on the hard drive.  From what I've read, the drive might survive less than 2 years if you do not address this issue.  See [https://bugs.launchpad.net/bugs/59695](https://bugs.launchpad.net/bugs/59695) for the gory details.  You will know if you have this problem, because the drive makes a distinctive clicking sound every few seconds when the machine is left idle.  I fixed this by adding "hdparm -B 254 /dev/sda" to my /etc/rc.local script.  If you've got a dual hard drive, you will need to add two lines, one for each drive (change /dev/sda to /dev/sdb).

Lambros

---

