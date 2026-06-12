---
title: "Open programs do not show when minimized"
date: 2009-02-15
forum: Desktop Environments
---

### Post by xtiano77 on 2009-02-15
I just noticed that when I minimize the window of an open program, the window seems to go to the bottom right section of the right monitor instead of showing in the bar that displays the trash bin and the icon that one clicks to minimize all screens at once. It didn't used to be like this earlier today.  Earlier today I was browsing around the net and when I minimized the window of any program, Firefox, Open Office, or the music player, the window would show minimized on the previously mentioned bar, but now for some reason, that is not the case.  Basically, if I minimize a window, I would have to start another session of that very program in order to access it again.  Any help would be really appreciated.

Also, as I mentioned earlier, I have a two monitor system. Both monitors now are ACER 193W. Previously I had two monitors as well, but the one on the left (main monitor where the applications bar is displayed) was an ACER 191W. The screen resolution on both monitors was 1440 x 900; however, after I replaced the ACER 191W with the ACER 193W, the startup, resolution of the new monitor changed to 1152 x 864 while the resolution of the older 193W remained at 1440 x 900.  I tried changing the resolution with the buttons on the monitor, but it seems as if it is being controlled by the OS. This makes the everything on the new monitor to show up proportionally larger and slower (everything displays on the left monitor about 2 to 3 seconds faster) all the way up to the log in screen.  Once I type the user's name and password, the resolution on both screens changes to 1440 x 900, but again it takes about 2 to 3 seconds for the left monitor to do that.  I there a script or command that can be run from the console that will make both monitors act the same?  I already tried switching the cables from one monitor to another and also the slot in which they are plugged into the graphics card, but the same monitor continues to do the same thing regardless of the cable or plug switch.  Thanks in advance for your help.  

System specs:

Ubuntu 8.10,64 bit
Two monitors
Intel Dual Quad
2 GB DDR2
ATI Radeon Graphics card

---

### Post by lhowaf on 2009-02-15
May be that the window list isn't showing. Look for a separator to the left of the one marking off the "tray" stuff (clock, etc). Right-click it, select Move and drag it over to see if the apps show (have an app running so you can see it).

---

### Post by xtiano77 on 2009-02-15
That was it!  I must have taken it out while playing around.  Thanks a bunch! How about the issue with the monitors?

---

### Post by lhowaf on 2009-02-15
Do you have the ATI drivers installed? Check out this solution for dual monitor issues (skip the driver install if you already have them). [http://www.v-nessa.net/2008/06/12/dual-monitor-setup-in-ubuntu-710-ati-radeon](http://www.v-nessa.net/2008/06/12/dual-monitor-setup-in-ubuntu-710-ati-radeon)

---

### Post by xtiano77 on 2009-02-15
I tried using the ATI drivers before and after the bootup, I couldn't see the screens, and so I had to re-install the OS. Before I try this, is there a way to bring back the current settings without having to re-install in the event that the ATI drivers don't work?  Sort of like the restore function in Windows?

---

### Post by lhowaf on 2009-02-15
This is referenced from the prior link for 8.10:
[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_manually)

The key seems to be to get the ATI Catalyst Control Center working and use that to set up the screens.

As far as saving your setup, you can do a general backup:
[http://ubuntuforums.org/showthread.php?t=81311](http://ubuntuforums.org/showthread.php?t=81311)

or you might just back up your xorg configuration (/etc/X11/xorg.conf). But read this first to make sure you can restore to the backup:
[https://answers.launchpad.net/ubuntu/+question/4273](https://answers.launchpad.net/ubuntu/+question/4273)

---

