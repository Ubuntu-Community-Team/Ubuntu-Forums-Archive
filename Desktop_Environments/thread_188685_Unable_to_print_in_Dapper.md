---
title: "Unable to print in Dapper"
date: 2006-06-04
forum: Desktop Environments
---

### Post by sargek on 2006-06-04
I have seen numerous issues about printing problems in Dapper, but no solutions. Printing worked fine in 5.10, but not at all in 6.06. Running a Samsung ML-1740, CUPS, and printing to the local port (/dev/lp0). Gnome config appears to configure the printer, but I still can't print. The printer either sits and does nothing, or starts to run then stops. I have the appropriate PPD file installed, and am able to add the printer via the Gnome interface. My web interface to CUPS is enabled and the printer shows as installed there as well. This is very frustrating - anyone have any solutions? Is CUPS 1.2 flat out broken? Thanks in advance.

---

### Post by Scunizi on 2006-06-08
I'm having the same issues but I own a ML-2010 Samsung laser.  I've had these problems since Flight 5 and printing is getting really annoying having to boot back to XP just to output paper.

---

### Post by bryanlking on 2006-06-09
I have a problem with my ML-2010 also, but it's not directly connected.  It's a network shared printer attached to another machine.  All network machines print to it just fine.  With the Ubuntu machine, I have to send the print command a minimum of two times for it to actually get the request through and print.  Once it prints, the output is fine.

It's strange that only the Ubuntu machine is acting that way.

---

### Post by Brando569 on 2006-06-09
i just cant install my printer at all, it says that it doesnt have the required module or i dont have the correct permissions when i try to install my HP PSC1610

---

### Post by sargek on 2006-06-09
I had to do a bit of experimentation to figure out what was wrong, but unfortunately I didn't come up with a solution. I tried Suse 10.1, but it seems to have CUPS 1.2 also so didn't work either - same issue: the printer spins for a few seconds and then stops. Fedora, with CUPS 1.1, works fine. I didn't want to go back to Breezy because the "official" version is now Dapper, and I would have had to ignore updates...

I am not sure if CUPS itself is at fault, or if it just doesn't like the .PPD files the Samsungs come with. I bought the Samsung specifically because it supported GNU/Linux, but that was a couple of years ago. Sigh...

---

### Post by ArponerO on 2006-06-09
Hi all,

I fixed the problem following this post:

[URL="http://launchpad.net/distros/ubuntu/+source/kdeprint/+bug/42965"]http://launchpad.net/distros/ubuntu/+source/kdeprint/+bug/42965
[/URL]

```
sudo foomatic-cleanupdrivers
``` 

Hope this helps

---

### Post by Scunizi on 2006-06-09
The link takes you to a KDE launchpad bug report.  I tried the suggestion about foomatic, uninstalled my ML-2010 driver and reinstalled.  The only change is I now get the printer que icon up next to my clock.  Are you running the KDE print system?  I'm on Dapper 6.06 gnome.  The bug reports mention that teh KDE print system may work under gnome.  Anyone with experience doing that?

bryanlking:  Is your remote printer on a windows box or linux?

This is really frustrating.  Too bad there isn't a simple answer or at least a step by step for us noobs with a little experience.  I think I've been reading about the cups system for over a month now and I'm no closer to an answer.

---

### Post by Scunizi on 2006-06-09
Of course..... it figures... ](*,)   Just after my last post I decided to revisit the foomatic web site referanced off [http://www.linuxprinting.org/cups-doc.html]("http://www.linuxprinting.org/cups-doc.html") and found a referance for the ML-1750.  It mentioned the mfg supplied PPD driver didn't work with all distros (duh) and to try a pxlmono or hpijs driver then specifically said to try the driver for the ML-4500.  VIOLA (as in ureka!)   all of a sudden my ML-2010 started working.  I was able to print a test page the page I was looking at in Firefox.  

I'm extreamly happy now.  Without printing Ubuntu was just an interesting exercise in new exploration.  It got the brain juices running on a technical bent again and feels good.  Now that I can actually be productive (with some limitations that STILL require XP) at least I won't find myself "boot flopping" on such a regular basis.

Now I'm off to figure out my Microtek ScanMaker 5950 w/sheetfeeder.  It also is not listed in the "functional" list of scanners.  I also need my ViCam web cam to work (for some reason v4l or others don't support it).  :rolleyes:

---

