---
title: "External Monitor - Acer X223w Display (No-sleep!)"
date: 2010-05-19
forum: Desktop Environments
---

### Post by A4orce84 on 2010-05-19
Hey Everyone,

I recently installed Ubuntu 10.04 on my desktop and finally got everything working ! (My network card would never work in 8.04 / 8.10, no matter how many DIYs and tweaks I did, so I was very surprised everything worked OOTB with 10.04!)

Anyway, everything works except my Acer X223W refuses to go to sleep (standby-mode) after 10 mins....even though I configured it to do so in the power management options.

I have a NVIDIA GeForce 8800GT graphics card running the "NVIDIA Accelerated Graphics Driver."

I leave my computer on a lot, so I was surprised my screen-saver was still running this morning and the monitor was not in sleep mode.

Anyone know what things to try and get this working?

Thanks in advance!


--Asif

---

### Post by cj.surrusco on 2010-05-19
**System>Preferences>Power Management** 

That should bring up a window with the option to set a sleep timer for the monitor.

---

### Post by A4orce84 on 2010-05-19
Tried that, no change. =(

---

### Post by A4orce84 on 2010-05-20
bump

---

### Post by A4orce84 on 2010-05-20
bump

---

### Post by A4orce84 on 2010-05-20
bump

---

### Post by A4orce84 on 2010-05-20
no one huh?

---

### Post by cj.surrusco on 2010-05-20
Check the nvidia driver settings. There might be an option in there.

---

### Post by A4orce84 on 2010-06-27
Did not fix the issue unfortunately.

Anyone else have any tips? =(

Thanks!


--Asif

---

### Post by PGHammer on 2010-06-28
> **A4orce84 said:**
> Did not fix the issue unfortunately.

Anyone else have any tips? =(

Thanks!


--Asif

It is definitely a display-driver issue; not one with the display itself.

I have the bigger brother of your display (Acer H233H.bmid; the twenty-three-inch model with HDMI support) and my Mom has the even larger H243H; neither has issues with sleep modes in terms of the display (my display properly shuts down after five minutes, which is Lucid's default setting).

---

### Post by A4orce84 on 2010-06-28
Is there a way I can try a different Acer monitor driver?

---

### Post by PGHammer on 2010-06-30
> **A4orce84 said:**
> Is there a way I can try a different Acer monitor driver?

Linux distributions have never used drivers for displays; X (first in XFree86, then X.org) used first settings in the respective configuration file (now /etc/X11/xorg.conf) then, if those were absent (some distributions, such as Fedora, no longer use this file at all) run an autodetection regime similar to that used by Windows (which, in only rare cases, normally doesn't use drivers for displays, either).

The default settings are passed to the OS in question via a VESA (Video Electronics Standards Association) standard method called EDID (Electronic Data Interchange for Displays).  While it was originally developed for CRT displays for computers, it has spread far (and wide!) beyond that connection to make its way into home-entertainment devices in general; also, while EDID was originally analog in nature, it can also be sent digitally (digital-only connections, such as DVI-I and HDMI, remain capable of passing along EDID information).  What EDID data 'buntu (or any OS that uses X) snags on bootup will be found in /var/log/Xorg.0.log, which makes this file important when it comes to troubleshooting display woes (the EDID data will be in roughly the middle of this log file, and will be in human-readable format).  Because this is information that Windows does *not* capture in human-readable format, someone that dual-boots Linux with Windows can find out more (often from this one log file) than a strictly Windows user would.

---

### Post by cbetts on 2010-06-30
I have been having a similar issue.  Running HP2035 monitors (TwinView) connected with an nVidia Quadro FX 560 card.  Found these lines in my Xorg log:
> (WW) Jun 07 07:15:15 NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
(WW) Jun 07 07:15:15 NVIDIA(GPU-0): Unable to read EDID for display device CRT-1

May be on to something here . . .

---

### Post by A4orce84 on 2010-07-08
Anyone have any new updates? I would really prefer if my monitor went to sleep instead of displaying the screen saver all night. =)

---

### Post by A4orce84 on 2010-08-21
bump

---

### Post by adam2007 on 2011-05-21
bump


same problem here: [http://ubuntuforums.org/showthread.php?t=1402436](http://ubuntuforums.org/showthread.php?t=1402436)
with a little more technical detail and a workaround script which I haven't tried.

there's an official bug report that still hasn't been resolved: [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/550054](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/550054)
but evidently the script is supposed to work

cheers

---

