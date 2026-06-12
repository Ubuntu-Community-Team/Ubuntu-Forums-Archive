---
title: "Linux Ubuntu desktop....?"
date: 2009-01-10
forum: General Help
---

### Post by Mountain Linux on 2009-01-10
Is there a way to make that little bar on the bottom that the Mac OS has?

I can't make my desktop effects work (for some reason...help?), so I don't know if I can do it... 

Are there any free drivers that I can download to make my desktop effects work? (or that little bar from the Mac OS)

---

### Post by the8thstar on 2009-01-10
The little bar you're referring to can be obtained with programs such as Cairo dock and AWN (Avant Window Navigator) which are in the repositories.

As for your desktop effects, what do you run? Ubuntu 8.10? Gnome? KDE? Is your computer recent or old? What graphics card does it have?

---

### Post by Mountain Linux on 2009-01-10
I have version 8.10

I installed it off the internet by putting Ubuntu on a disk and installing it on my acer. I used to have windows but I removed it.

How do you find out the graphics card? If you mean by some bought graphics card, I don't think I have any.

---

### Post by the8thstar on 2009-01-10
Well, let's have a look.

Go to Applications > Accessories > Terminal. At the prompt enter the command :

> lspci


That should tell us what hardware you have on your computer.

---

### Post by Mountain Linux on 2009-01-10
> 00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0b:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

That what I get. Can you make any sense outta this?

---

### Post by the8thstar on 2009-01-10
Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

This means you have an Intel 945GM Graphics Card, like I do on my computer.

Now, to activate the desktop effects, right click on the screen (not in an open window) and select "Change Desktop Background". Then select the "Visual Effect" tab and choose the setting you prefer. If all goes well you should be all set.

For the dock thingy, go to Applications and select "Add/Remove". In the search bar, look for Avant Window Navigator.

---

### Post by Mountain Linux on 2009-01-10
Yes, I always do that. I tried all of the settings and it searched for the drivers at first and closed when it was at 0% and it says that the effects could not be enabled. Are some of my drivers missing?

---

### Post by the8thstar on 2009-01-10
This could be because the installation was corrupt in some way. You could try and reinstall Ubuntu altogether or wait for another poster to respond. Personally I never encountered this sort of problem on my machine, which has a graphics card similar to yours.

---

### Post by Mountain Linux on 2009-01-10
Well yeah, but then my network connection will be messed up again. I gotta re configure it again...


Oh by the way, the "Extra" used to work on the first week of my Ubuntu, but now it doesn't. That's the weird thing...

Oh and also, most of my screensavers don't work either...

---

### Post by jesterthejedi on 2009-01-10
You may need to enable the drivers in the menu.

Menu > System > Admin > Hardware Drivers

If there are any in the dialog box, try enabling them and do a CTRL + ALT + Backspace. I also have an Acer with the same 945 Intel chip. Your next step will be installing CCSM and trying ALT + F2 and type in "compiz --replace" to get it going.

---

### Post by Mountain Linux on 2009-01-10
I have pretty much everything for compiz, but the real problem is my desktop effects and my drivers. They won't be enabled. My backgrounds and themes work fine but it's my desktop effects and my screensavers too that have problems. They won't appear.

---

### Post by jesterthejedi on 2009-01-10
Check out this post:

[http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

Also can you enable the basic effects?

---

### Post by Mountain Linux on 2009-01-11
If you're talking about "Normal" effects, then no. I can't enable any effects (normal, extra, custom)...

---

### Post by jesterthejedi on 2009-01-11
What was the results of the compiz check?

---

### Post by Mountain Linux on 2009-01-11
Compiz-check?

I can't do it. It says the command doesnt exist (something like that). Do I have to be on (name)-desktop or (name)-laptop?

---

### Post by jesterthejedi on 2009-01-11
Save the file to your desktop. Here is what commands you need to do in a terminal:

cd Desktop "enter"
./compiz-check "enter"

attached my screenie

---

### Post by Mountain Linux on 2009-01-11
"No such file or directory was found"

I got to the desktop thing, then I typed in that ./compiz-check thing.

I tried it without the period too...

What now?

---

### Post by jesterthejedi on 2009-01-11
Did you save the compiz-check file on your desktop? I put it in the attachments above. You may need to make it executable, so right click on it, and go to properties, permissions, and make sure the Execute box is checked. Also the period is required!

---

### Post by Mountain Linux on 2009-01-11
I saved it to my desktop.

I checked the permissions box too. No such file or directory...

---

### Post by jesterthejedi on 2009-01-11
Did you extract the file?

---

### Post by Mountain Linux on 2009-01-11
ok so I got it. Heres the results...:

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect maximum 3D texture size

---

### Post by jesterthejedi on 2009-01-11
hit ALT + F2 and type in "compiz --replace" then enter and rerun the compiz-check.

---

### Post by Mountain Linux on 2009-01-11
Isn't that the "real" terminal? How do I exit that terminal then?

Can't I do compiz --replace in the "mini" terminal without the alt f2?

---

### Post by jesterthejedi on 2009-01-11
No thats the Run box, kinda like windows has one on Start > run. The benefit is you can start stuff and not have to quit the program when you close a terminal.

---

### Post by Mountain Linux on 2009-01-11
I got the exact same results as last time...

---

### Post by jesterthejedi on 2009-01-11
I'm looking up some more tips. Do you have a messenger to chat on?

---

### Post by Mountain Linux on 2009-01-11
I have a yahoo mail account. I think that has a messenger on it...

---

