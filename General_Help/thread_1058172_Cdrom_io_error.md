---
title: "Cdrom i/o error"
date: 2009-02-02
forum: General Help
---

### Post by Schwalenberg on 2009-02-02
All of the sudden my CD-ROM drive keeps giving me I/O errors at random times throughout re-install processes. My GUI is down because of a bad update to an Nvidia restricted driver and as a Linux newbie I am feeling a bit cornered on this machine. I can load server 8.10 with the cd in the drive, but half-way through the process I get an I/O error. I made another CD just to rule out a bad CD, but the exact same I/O error message came up. I have root access on the computer, but I cannot seem to figure out how the last batch of updates cost me my CD-ROM drive and my GUI. I can load firefox --display :0 and hit control-alt-f7 and it works flawlessly, but there is no desktop behind it. I have been trying to get gdm working again by re-installing it or the nvidia drivers, not sure which is the culprit but neither will re-install without the cd, and my cd-rom keeps saying there is an I/O error which I have never had any issue with previously... Why does it say there is paperjam WHEN THERE IS NO PAPERJAM!

---

### Post by lavinog on 2009-02-08
Have you checked the integrity of the CD with the "Check CD for defects"?
Is the drive old? Sometimes drives go bad, or get dusty.
Also check your memory too with the memtest

---

### Post by Schwalenberg on 2009-02-08
> **lavinog said:**
> Have you checked the integrity of the CD with the "Check CD for defects"?
Is the drive old? Sometimes drives go bad, or get dusty.
Also check your memory too with the memtest


   No, I am new to Linux and did not even know that existed but I did try other CD's that had the same error which leads me to believe it is a hardware issue. I was able to artifically mount a downloaded .iso and fix most of the other issues I had except the CDROM is obviously still not working and for some reason I still cannot figure out why the GNOME GUI Desktop is blank (pure black). 
   It says there is an install error with the power management utility, which I suppose I should have addressed that head-on but I do not even know the name of the utility to repair it. I tried uninstalling and reinstalling gnome altogether with no change. Like I said earlier I can load up a program like firefox on --display :0 with no issue but have no desktop / menu bar or anything else.
    Does this mean GNOME is not loading at all or just improperly? I guess what I mean to ask is if GNOME was never installed could firefox be run stand alone on that display? I should probably be posting these as two seperate issues because they are but oh well. I was not expecting to get so much into this so fast. I wanted to stick mostly to the GUI and the terminal in there instead of pure command prompt but the experiance I have gained from this is priceless I would not go back in time and change it now if I could :popcorn:

---

### Post by lavinog on 2009-02-08
The multiple issues would tell me you had a corrupted install. The amount of information that is on the cd makes a corrupt cd very unpredictable.

All that is required for firefox is X. It provides the gui while gnome provides some of the more advanced window/desktop features.

Usually to troubleshoot a problem with the GUI, you should look/post /var/log/Xorg.0.log
But I would recomend looking into checking your install disk...if the problem is due to a bad install, you may want to reinstall. If you cant seem to burn a good disk, the problem may be your cd drive...you can try and order the cds for free or try a different drive.

---

### Post by Schwalenberg on 2009-02-09
I think it was a corrupted update. Because everything worked fine until the last update. Even my CDROM drive... After the update I went for the reboot and lost both my GUI and my CDROM drive started having this same I/O error no matter what CD gets put in there. I tried the undo last update recovery option to no avail (it was unable to revert). I just realized that maybe XDM was never setup properly to begin with since I used GDM and now that GDM will not boot-up maybe thats the issue. The impression I got originally was that GDM was its own GUI and had nothing to do with x-windows. However, it was just a replacement for XDM and now it is not working maybe XDM doesn't look right because it was never setup properly to begin with...

---

