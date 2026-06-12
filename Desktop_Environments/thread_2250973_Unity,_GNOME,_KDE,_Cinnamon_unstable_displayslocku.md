---
title: "Unity, GNOME, KDE, Cinnamon unstable displays/lockups"
date: 2014-11-01
forum: Desktop Environments
---

### Post by carlwsnyder on 2014-11-01
I have been fighting this problem since 10.10 and finally found MY solution.  I reported this as Ubuntu Unity bug [lpbug]756818[/lpbug], which has the hardware configurations I had (two different computers).  Since this happened to me with 2 different computers and 2 different monitors, I thought I would report this here, so that someone else might be helped.

Windows never had a problem with the Etronix 1701B 1280x1024 monitor which I bought from a local OfficeMax about 10 years ago, but the Linux drivers have given me fits since I first switched in 2007.  Although Knoppix 5.11 and later would actually run well, and the Live Ubuntu disks with GNOME 2, LXDE, Mate, and Xfce worked fine, when Unity came out, KDE 4, and/or GNOME/Cinnamon, I would barely get a usable display, if ever, even with proprietary drivers, and I was always having to manually set the proper display resolution to the maximum for the monitor, because the EDID was either not being read properly or was not formatted properly for this monitor.  This meant that I learned a lot about first **/etc/X11/xorg.conf** , then later when **xrandr** became the default, about that method of setting the display resolution.  I was able to help several people with their display problems on these forums and other places, but only certain desktops were usable.  I usually used the **nouvea** open-source drivers, because those worked better for me on the desktops which were usable at all.

Symptoms: I might or might not get a proper initial desktop display, but the second I tried to use the display, I would have one of three results:
[LIST=1]
[*]most likely, I would have random scan lines on the display with patterned color dots to start, if this lasted long enough to see, then those  scrambled dots would fill the entire screen, and the only reports after the fact were of a GPU panic.  Full-lockup usually resulted, Keyboard Ctrl-Alt-Scroll Lock REISUB reset ineffective, Ctrl-Alt-Fx CLI desktops unavailable, only a hard reset or power cycling was able to restore control of the computer.
[*]second most likely, attempting to enter the desktop would simply fill immediately with the semi-random pattern of dots, rendering any mouse movements and/or keyboard entries invisible.  Most of the time, I was even unable to get to a Ctrl-Alt-Fx CLI desktop to recover, or to use the REISUB reset, although sometimes one or the other worked.
[*]This result was frustrating in the extreme, and _almost worked:_ I would get white on yellow text with mainly white on yellow background.  If I was able to open a terminal and install nvidia-current, my colors would be restored and I may get what looked like a usable desktop.  I may even be able to use Firefox/Chromium/Google Chrome to browse the web or another application for a while.  Terminal was usually the most stable once I got the colors fixed.  But then something would happen, and I was back to either result 1 or 2.
[/LIST]

I kept trying, with no good result, until this morning I swapped in a new monitor, a Sansui SLED 2900I television, 1920x1080, 1080p capable, to see if that might solve the problem.  The results at first were mixed: I was getting either result 2 or 3 when running the problem desktops in Live mode or when using one of my Xubuntu x64 installations with GNOME 3.x installed to check it out (Xubuntu 14.04).  I decided to try installing **nvidia-current** proprietary driver to check it out for better results.

BINGO!  With the new display, which has a valid EDID, and with the **nvidia-current** proprietary driver package, both GNOME and Unity desktops are, at least at present, operating without problems.  I seem to have had a two part hardware/driver problem.

I am going to check out KDE and Cinnamon to see if those are also working properly, but I expect good results for those as well.

---

### Post by kurt18947 on 2014-11-01
I haven't had your problems but I am finding that with a current Nvidia 210 based video card, the nouveau driver doesn't work as well as the proprietary Nvidia driver.  XFCE works okay, Ubuntu Gnome works but not well using the Nouveau driver.

---

### Post by carlwsnyder on 2014-11-07
Update: KDE & Cinnamon DEs do work also.  Had to downgrade from nvidia-current to one of the -legacy drivers, depending on the distro, for my motherboard video, a nVidia C61 (equivalent to GeForce 7025 or nForce 630a).

THIS IS NOT TO COMPLAIN ABOUT nouveau!!!  Nouveau was the only thing that worked well with my Etronix 1701B/bad reported EDID.

Note: This bug affected Live boot disks which booted into Unity, GNOME 3.x, etc. as well as full installations.

I am aware that there are methods for substitution of a fixed EDID, but I ever worked on that solution long enough to get it functioning.

---

