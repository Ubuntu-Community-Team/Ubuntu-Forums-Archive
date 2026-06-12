---
title: "Compiz problems"
date: 2009-09-20
forum: Desktop Environments
---

### Post by dave11980 on 2009-09-20
Got a bit of an odd problem I'm hoping you guys can help out with.  I recently installed 9.04 and had it working wonderfully with full desktop effects enabled on two users, mine and my wifes.  After about 2 days I am now only able to get it working on 1 user at a time, which ever user logs in first after reboot.  The other user gets the desktop effects could not be enabled error.  I've tried starting compiz from the cli as well and get the below output.

compiz cli output:
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity 



This is all running on a dell dimension 4700 with intel graphics.

dbrewer@dell:/var/log$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation 82915G Integrated Graphics Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
03:01.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)
03:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 03)



Let me know if you need anything else to help out.

---

### Post by dave11980 on 2009-09-26
I'm still having this problem.  Anyone have any ideas?

---

### Post by baskar007 on 2009-09-26
> **dave11980 said:**
> I'm still having this problem.  Anyone have any ideas?
reinstall compiz,  I have same problem on my Pc with intel card. After reinstalling Compiz the prob gone!!!

---

### Post by cgroza on 2009-09-26
You added compiz to group...

---

### Post by dave11980 on 2009-09-26
> **cgroza said:**
> You added compiz to group...

I'm not sure I follow you there.  Can you elaborate?

---

### Post by dave11980 on 2009-09-26
One thing I did find out on the tubes is that when a second X server is started on intel graphics cards it doesn't get DRI support.  I indeed have two X servers running when both users are logged in.

root      2596  2593  3 14:18 tty7     00:00:22 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
root      3847  3842  1 14:24 tty9     00:00:03 /usr/bin/X :20 -br -audit 0 -auth /var/lib/gdm/:20.Xauth -nolisten tcp vt9


I couldn't be certain without reinstalling but I am close to certain that this did work a week ago when I first installed and stopped working sometime a couple days later.  I also read that the guest session starts a separate x server and that xnest does as well, both things i have done.  I've uninstalled xnest but I think there may be some setting from either the guest session or from xnest that is lingering and forcing new users to spawn new xservers.  Anyone have any ideas on this?  Or am I full of crap?  I am fairly new to 'desktop' Linux.

---

### Post by dave11980 on 2009-09-26
> **baskar007 said:**
> reinstall compiz,  I have same problem on my Pc with intel card. After reinstalling Compiz the prob gone!!!

I did a full apt-get purge on all compiz packages, restarted computer, and then apt-get install.  I'm still seeing the same problem.  

From the other things I've been reading this has to do with intel drivers not providing DRI to any x servers after the first.  I've confirmed in my /var/log/Xorg.20.log that the second xserver doesn't have DRI.  The question now is this, is it possible to configure multiple users to share a single xserver instance in ubuntu 9.04, and how?

---

### Post by fuzetsu490 on 2009-09-26
Im not an expert but i had a similar problem and what i did was start up in kernel mode (i think thats what its called) then i chose to "automatically fix display errors" (once again i think thats what it says or at least something similar) after that it worked fine as well as fixed my other problem with my Xorg.conf (i was editing it and i did something wrong, when i rebooted my display wasnt working all i got was a black screen = = )

---

