---
title: "Optiplex 740 install failure w/ - 9.10, 10.04 &amp; 10.04.1"
date: 2010-08-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Baji P. on 2010-08-26
This applies to both 64-bit CD images, Live & Alternate. I have not tested to see if the server CD image works. Also experienced this with a kubuntu CD.

32-Bit CD images of 10.04.1 (Lucid) installed fine.

When I used a 64-bit CD from Lucid or Karmic, I get the language selection menu, upon choosing a language, I can test memory. But I could not check the CD for defects or "Install Ubuntu". The screen clears and the system just hangs. I was able to successfully use the same CD on another 64 bit machine, that was not an optiplex 740.

To install 64-bit Ubuntu/Kubuntu on a Dell Optiplex 740 with a 64-bit AMD processor, go all the way back to a 9.04 64-bit CD image (preferably alternate).

9.04 installs successfully, then upgrade to 9.10 from the Update Manager, followed by an upgrade to 10.04.1.

There are minor differences in directory structure between  9.04 & 10.04, but that is a small penalty for the advantages of being able to run a 64-bit kernel on these machines.

If some one can figure out could what changed in the install program from 9.04 to 9.10 that broke the 64-bit install, perhaps we can get a fixed future release.

Thanks to **[RayRuest]("http://ubuntuforums.org/member.php?u=259017")** & **[JinxCrossbow]("http://ubuntuforums.org/member.php?u=1108483")** for coming up with this solution by trial & error :)

-baji.

---

### Post by Baji P. on 2010-08-28
In case the nVidia display adapter is the cause, here is the output from : 

           hwinfo --gfxcard

19: PCI 05.0: 0300 VGA compatible controller (VGA)              
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_10de_241
  Unique ID: CvwD.NTCHND2S26F
  SysFS ID: /devices/pci0000:00/0000:00:05.0
  SysFS BusID: 0000:00:05.0
  Hardware Class: graphics card
  Model: "nVidia GeForce 6150 LE"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x0241 "GeForce 6150 LE"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x01ec 
  Revision: 0xa2
  Driver: "nvidia"
  Driver Modules: "nvidia"
  Memory Range: 0xfc000000-0xfcffffff (rw,non-prefetchable)
  Memory Range: 0xe0000000-0xefffffff (rw,prefetchable)
  Memory Range: 0xfb000000-0xfbffffff (rw,non-prefetchable)
  Memory Range: 0xf4000000-0xf401ffff (ro,prefetchable,disabled)
  IRQ: 16 (3158806 events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v000010DEd00000241sv00001028sd000001ECbc03sc00i00"
  Driver Info #0:
    XFree86 v4 Server Module: nv
  Config Status: cfg=new, avail=yes, need=no, active=unknown

Primary display adapter: #19

thnx.

-baji.

---

### Post by Baji P. on 2010-09-06
I DO NOT recommend the  9.04 => 9.10 => 10.04.1  upgrade route, to get 64 bit Ubuntu on a OptiPlex 740 or any other machine.

The resulting install is not very stable, X drops out of GUI from time to time.

The latest versions of a few programs like Chrome & Firefox run into minor annoyances because folders like ~/Downloads & ~/Pictures don't exist, or are not located where 10.04.1 expects them to be.

ext4 was not fully matured when 9.04 was released, so you have to wonder what bugs are getting carried forward when you upgrade from 9.04 to 10.04.1

I scrapped my 64 bit install and went back to 32 bit alternate 10.04.1 CD, the process was very smooth and the resulting installation is very stable and suitable for production use. But it only sees 3.5 Gig out of my 4 Gig memory.

This is an all round tragedy that in 2010, even though 64 bit processors have been around for many years, for a stable install we are still stuck with 32 bit.

---

### Post by Baji P. on 2011-02-13
:D
I am happy to report that both Ubuntu & kubuntu 10.10 x64 images installed successfully on my Dell Optiplex 740 ( 4 Gig ram, dual core athlon processor ).

After installing, I ran the following command (from my previous 9.04 desktop) and all my data, preferences, bookmarks & passwords moved over to the new 10.10 desktop in about 20 minutes :

scp -rp /home/xxxx xxxx@[new-host-ip]:/home/

Replace xxxx with your login.

---

