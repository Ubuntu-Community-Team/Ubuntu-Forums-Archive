---
title: "VirtualBox and 3d Acceleration"
date: 2008-12-19
forum: Gaming &amp; Leisure
---

### Post by compiledkernel on 2008-12-19
Sun released xVM 2.1, and it has experimental support for 3d. So whos going to try it and see just how good it works? 

from the changelog -- 

    * Support for hardware virtualization (VT-x and AMD-V) on Mac OS X hosts
    * Support for 64-bit guests on 32-bit host operating systems (experimental; see user manual, chapter 1.6, 64-bit guests, page 16)
    * Added support for Intel Nehalem virtualization enhancements (EPT and VPID; see user manual, chapter 1.2, Software vs. hardware virtualization (VT-x and AMD-V), page 10))
    * **Experimental 3D acceleration via OpenGL (see user manual, chapter 4.8, Hardware 3D acceleration (OpenGL), page 66)**
    * Experimental LsiLogic and BusLogic SCSI controllers (see user manual, chapter 5.1, Hard disk controllers: IDE, SATA (AHCI), SCSI, page 70)
    * Full VMDK/VHD support including snapshots (see user manual, chapter 5.2, Disk image &#64257;les (VDI, VMDK, VHD), page 72)
    * New NAT engine with signi&#64257;cantly better performance, reliability and ICMP echo (ping) support (bugs #1046, #2438, #2223, #1247)
    * New Host Interface Networking implementations for Windows and Linux hosts with easier setup (replaces TUN/TAP on Linux and manual bridging on Windows)

---

### Post by crazyfuturamanoob on 2008-12-19
Maybe I could put a ps2 bios in that vm and see if I can use it just like a ps2?

---

### Post by derekr44 on 2008-12-19
Downloading it to upgrade now :).  I've got it running here at work.  I'll try out how Compiz works on it just to see.

---

### Post by compiledkernel on 2008-12-19
Derekr44 - Probably wont work, the guide says 3d only works on Windows Guests (and Vista 32-bit guests, but there cant be that many of those).

---

### Post by derekr44 on 2008-12-19
Bummer.  I'm here at work and thought I'd give it a shot on my Virtual-Linux.

Was worth a try :)

---

### Post by eragon100 on 2008-12-19
Can't you run Compiz under KDE 4 for windows? You can atleast try and see if KWin's effects work if you do that :wink:

---

### Post by mikedep333 on 2008-12-19
Don't get your hopes up that you can run every windows game now.

[2.1.0 Manual Link]("http://dlc-cdn-rd.sun.com/c1/virtualbox/2.1.0/UserManual.pdf?e=1229655794&h=10f7f41be9612fdaba775e1a233e47ca")

> With this new feature, if an application inside your Windows guest uses 3D features through the OpenGL programming interfaces, these will not be emulated in software (which is slow), but instead VirtualBox will attempt to use your host&#8217;s 3D hardware. This works for all supported host platforms (Windows, Mac, Linux, Solaris), provided that your host operating system can make use of your accelerated 3D hardware in the &#64257;rst place.

> The 3D acceleration currently has the following limitations:
**1. It is only available in Windows XP and 32-bit Vista guests with the Windows Guest Additions installed.**
**2. Only OpenGL acceleration is presently available in those guests; Direct3D is not yet supported and will be added in a future release.**
3. Because the feature is experimental at this time, it is disabled by default and must be manually enabled in the VM settings

> Technically, VirtualBox implements this by installing an additional hardware 3D driver inside your Windows guest when the Guest Additions are installed. This driver acts as an OpenGL hardware driver and reports to Windows that the (virtual) hardware is capable of 3D hardware acceleration.

> Linux hosts. There are a few problems when compiz is used as the host&#8217;s window manager, notably:
&#8211; seamless mode does not work well (garbled screen display if no windows are open in the guest);
&#8211; OpenGL guest acceleration (added with 2.1) is very slow.

So you may want to read this wikipedia list of OpenGL games, as only OpenGL games are likely to work.
[http://en.wikipedia.org/wiki/OpenGL#OpenGL_Games](http://en.wikipedia.org/wiki/OpenGL#OpenGL_Games)
I should add to the list that Call of Duty and Call of Duty 2 are openGL and therefore are likely to work.

Here is a virtualbox.org thread on games that work.
[http://forums.virtualbox.org/viewtopic.php?t=2525&postdays=0&postorder=asc&start=49](http://forums.virtualbox.org/viewtopic.php?t=2525&postdays=0&postorder=asc&start=49)
> Warcraft III (have to be run with -opengl command line option): [IMG]http://img209.imageshack.us/img209/1368/wc3hb9.th.jpg[/IMG]

---

### Post by compiledkernel on 2008-12-19
While probably not the best test model, i used OpenArena for testing purposes. 

For the sake of reference, this is on a duo core 2.6x proc, with 2 gig of memory, and a 256meg PCIex Nvidia card. I maxed out the video memory to 128 megs, and selected 3d Acceleration. The VM memory base is 315, I could rebenchmark at a higher rate if anyone would like for their own edification. 

I was averaging 70ish FPS , and in heavy action, 40ish FPS.

SideNote: This is with all effects turned to low, and textures turned to low (which I would do anyway, so may not be your cup of tea).

---

### Post by mikedep333 on 2008-12-19
> **compiledkernel said:**
> While probably not the best test model, i used OpenArena for testing purposes. 

For the sake of reference, this is on a duo core 2.6x proc, with 2 gig of memory, and a 256meg PCIex Nvidia card. I maxed out the video memory to 128 megs, and selected 3d Acceleration. The VM memory base is 315, I could rebenchmark at a higher rate if anyone would like for their own edification. 

I was averaging 70ish FPS , and in heavy action, 40ish FPS.

SideNote: This is with all effects turned to low, and textures turned to low (which I would do anyway, so may not be your cup of tea).

There are native binaries of OpenArena for Linux. Assuming the same version isn't in the ubuntu repos, you can either download the zip from their website, or use getdeb.

So please test it under Linux using the same settings

And keep in mind, my Geforce 8800GT pci-e 256 MB is probably 15x as fast as the lowly Geforce 6200 pci-e 256MB. Video memory is a very poor indicator of performance.

---

### Post by eragon100 on 2008-12-19
> **compiledkernel said:**
> While probably not the best test model, i used OpenArena for testing purposes. 

For the sake of reference, this is on a duo core 2.6x proc, with 2 gig of memory, and a 256meg PCIex Nvidia card. I maxed out the video memory to 128 megs, and selected 3d Acceleration. The VM memory base is 315, I could rebenchmark at a higher rate if anyone would like for their own edification. 

I was averaging 70ish FPS , and in heavy action, 40ish FPS.

SideNote: This is with all effects turned to low, and textures turned to low (which I would do anyway, so may not be your cup of tea).

Can you test with homeworld 2, that game also has an OpenGL version and is much more demanding than quake 3? :wink:

(If you can't, I will test it one of the coming days and report the results :))

---

### Post by binbash on 2008-12-19
@mikedep333 

thanks for the virtual box game list link!!!! I was looking for that

---

### Post by compiledkernel on 2008-12-19
> **mikedep333 said:**
> There are native binaries of OpenArena for Linux. Assuming the same version isn't in the ubuntu repos, you can either download the zip from their website, or use getdeb.

So please test it under Linux using the same settings

And keep in mind, my Geforce 8800GT pci-e 256 MB is probably 15x as fast as the lowly Geforce 6200 pci-e 256MB. Video memory is a very poor indicator of performance.

I was aware of the native nature of OpenArena, Mike, I used it as a litmus for what I thought would be just a good indicator, so I grabbed the simplest of games I thought windows would run on limited hardware, in this case OA. I wasnt necessarily using it to say "Hey the Vbox install runs much faster than the native install". That would be a crazy assumption really. 

Eragon, I have a copy of HW2, so I have no problem testing it either if you would like.

Side note: Mike, my card is a 7800 Go, not a 6200.

---

### Post by mikedep333 on 2008-12-19
> **compiledkernel said:**
> I was aware of the native nature of OpenArena, Mike, I used it as a litmus for what I thought would be just a good indicator, so I grabbed the simplest of games I thought windows would run on limited hardware, in this case OA. I wasnt necessarily using it to say "Hey the Vbox install runs much faster than the native install". That would be a crazy assumption really. 

Eragon, I have a copy of HW2, so I have no problem testing it either if you would like.

Side note: Mike, my card is a 7800 Go, not a 6200.

OK, wow

So a game like OpenArena, which requires like a Geforce 6200 to run natively, probably needs more like a 6600GT to run virtualized.

---

