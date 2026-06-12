---
title: "Printing With 2335dn"
date: 2010-01-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by MBLGUY80 on 2010-01-03
Does anyone have any idea how to make the 2335dn printer work on Ubuntu 9.10?  I see that the version of the printer just below this one (2330dn) has its own ppd files provided by Dell.  Do we need to contact Dell about getting those?

I tried installing the software via Crossover.  That didn't work.  I haven't tried directly plugging it into the computer as a USB connection because I prefer to have it as a network printer.  It has a static IP so if I can just print to an IP address that would work as well.

Any suggestions?

Thanks!

---

### Post by prshah on 2010-01-04
> **MBLGUY80 said:**
> Does anyone have any idea how to make the 2335dn printer work on Ubuntu 9.10?

I have not worked with this printer before, but I have set up multiple types of digital copiers from Canon, Xerox et al, and I assume this will function in the same way. My assumption may be wrong.

You need to get certain information about how the copier is setup. You need the IP address of the copier, and the "Queue" name; both of these will be displayed in the configuration sheet. The configuration sheet can be printed by selecting suitable options on the copier (sorry, don't have more details).

If you cannot find the Queue name, then here's something to try. From a Windows system, click Start-Run, and give the command```
\\192.168.1.57
``` please replace the given IP address with the IP address of the printer. You should have a window open up shortly with (typically) 3 queues, called (typically) Print, Hold and Resume. You will usually use the Queue called Print. If you do not get such a window and cannot find any reference to a print queue, then the printer probably does not work in the same fashion as a digital copier, and it would be pretty pointless for you to continue with these instructions. :(

Once you have the required information, open a browser on the Ubuntu system. In the address bar, type ```
http://localhost:631
``` to open the CUPS (Common Unix Printing System) page.

If at any point CUPS asks for a username and password, give the username and password of any sudo capable user on the system.

On the CUPS main page, choose the "Administration" tab. Then choose "Add printer". From the options for network printing, choose "LPR/LPD Host or printer", and choose Next (Continue?). When asked for the "Connection", please enter```
    lpd://ipaddress/queuename
``` where ipaddress and queuename are taken from the configuration sheet. Choose Next/Continue.

Give the printer a name, and fill in whatever other information you feel relevant. Continue. 

In the next screen, provide a .PPD file if you have it available on the driver disk. If you have a PPD file, enter it's location and choose "Add printer".

If you don't have a PPD file, choose the closest matching printer from the "Make" and "Model" options. Click "Add Printer" when done. 

Set your default options as suitable to you, including paper sizes, tray options, etc. 

Now your printer should be working fine. Please try a test page, and post back here if you have any problems.

---

### Post by MBLGUY80 on 2010-01-04
Thank you so much!  For those of you out there that need drivers, please see Dell's website and search for the drivers for the 2330nd laster printer.  It's the model right below mine with little to no differences.  Mine works great following these instructions!

Once again, thank you for helping me with this!

---

