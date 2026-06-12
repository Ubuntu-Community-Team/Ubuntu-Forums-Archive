---
title: "Ubuntu is running in low graphics mode - graphics problem"
date: 2010-05-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by foreverNewbie on 2010-05-29
Hello, 

I am linux newbie and decided to give Ubuntu a shot.  I have a Dell Dimension E310 with an onboard graphics card.  CPU is a Pentium 4 3.2GHz

I had all types of problems installing Ubuntu with a CD (which I now think is related to my graphics card since it went blank during installation, although there were other problems) so I went to Wubi-installer.com and did it that way (not exactly installed but I'm able to try it out).   

After installing I still can only run in failsafe graphic mode.  If I don't run in this mode, I just get a blank screen.  When Ubuntu finally shows something , it says:
"Ubuntu is running in low-graphics mode.  Screen, Graphics card & input device settings could not be detected corrected"

There is a menu where I can select "Reconfigure Graphics" but it just brings me back to the menu.  There is another menu which lets me look at the XServer log file & the Startup Errors but both files are empy when I look at them.  Also, "Edit Configuration File" only brings me back to the menu.  

I have attached a picture of the Monitor preferences which shows only an unknown monitor.  

I'm not sure what other information anyone might need but I'm sure i've left some information.  Please let me know any other information that might be useful.  

Any help would be much appreciated.

---

### Post by foreverNewbie on 2010-05-29
Was just reading another thread and I got the output from lspci

00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
03:02.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 61)
03:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 04)

---

### Post by bildr on 2010-05-29
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

[http://absolutebeginner.wordpress.com/2006/07/26/installing-intel-815852855-graphics-controller-drivers-on-ubuntu-debian/](http://absolutebeginner.wordpress.com/2006/07/26/installing-intel-815852855-graphics-controller-drivers-on-ubuntu-debian/)

---

### Post by foreverNewbie on 2010-05-31
so I tried downloading the intel drivers and installing them as what was described in the 2nd link but that didn't seem to make a difference (there didn't appear to be any errors when installing but I guess I could have missed something).  

newbie question: do I need a xorg.conf file?  at first there wasn't one so I copied the one from the 'default file' from [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) but that didn't seem to make a difference.  

the output from xrandr is:
leroy@ubuntu:~$ xrandr
Screen 0: minimum 1280 x 1024, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024       0.0* 

looks like only 1 resolution available.  

i'm pretty sure i missed something so any help would be much appreciated.

---

### Post by foreverNewbie on 2010-06-01
for the time being, i've copied xorg.conf.failsafe into xorg.conf

anyone have any ideas?

---

### Post by mvelte54 on 2010-06-05
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)

Not sure what version of Ubuntu you are running but I am running a Dell Inspiron mini 10 with the desktop version of 9.10 Karmic Koala running on it and I also had trouble with the graphics. i.e. No special effects just a very plain configuration and I too had to run in 'safe mode'. I found this and thought I would give it a try. Problem solved. for me anyways.
Good luck, don't be afraid to experiment just back up everything you consider important incase you need to reinstall.

---

### Post by foreverNewbie on 2010-06-07
thanks mvelte54!

i will take a look.  as for version of ubuntu, i'm running 10.04.  

i didn't realize that there were different portions that could be broken & working.  

The one thing I'm wondering is whether this applies to me - whether i'm running Intel GMA500 "Poulsbo" video hardware.

I was starting to think that I would have to start looking at building the drivers myself but I think that would be a large amount of work and I could really screw things up.

---

### Post by marcoftheknight on 2010-06-07
Hi just wanted to let you know a way to check and see if it's recognizing the driver you recently install is to use the 

lshw ( list hardare scroll to the integrated graphics part and it should show a hole bunch of details including the driver your using for that particular peice of hardware got to love ubuntu!

FOR example:
THis shows im using fglrx for my video driver and HDA intel driver for my digital out AUDIO.

*-display
                description: VGA compatible controller
                product: Juniper [Radeon HD 5700 Series]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:31 memory:d0000000-dfffffff(prefetchable) memory:fdec0000-fdedffff ioport:ee00(size=256) memory:fde00000-fde1ffff(prefetchable)
           *-multimedia
                description: Audio device
                product: Juniper HDMI Audio [Radeon HD 5700 Series]
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:30 memory:fdefc000-fdefffff

---

### Post by dmurphy787 on 2010-08-16
I also have Ubuntu running in low graphics mode and I have spent about 3 hours so far, scouring the forums following code inputs with no success.  I wanted to love Ubuntu Linux but the problems are just to hard to fix without knowledge and I have extensive windows knowledge and abilities.  I really want to succeed with loving Linux but I can't see a solution, this is the second reinstall I have had to do in 2 weeks because of unfixable errors.  Can anyone give me hope?  PLEASE!!!!!!!!

---

### Post by RockTeam on 2010-12-21
Each time after booting up from hibernation I see notification that "Ubuntu  is running in low-graphics mode". I can not resolve it myself. I suppose  that the problem is in incorrect video driver or something else. My PC is Acer D260 with Xubuntu 10.04. Video adapter is GMA 3150.

I haven't xorg.conf file in /etc/X11/ but I see xorg.conf.failsafe:

```
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "fbdev"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```  Could you please share your experience how to resolve this problem? Please let me know if more information are required.

```
root@acer:~# lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

root@acer:~# lshw
     *-pci
          description: Host bridge
          product: N10 Family DMI Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: N10 Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:27 memory:58180000-581fffff ioport:60c0(size=8) memory:40000000-4fffffff(prefetchable) memory:58000000-580fffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: N10 Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:58100000-5817ffff
```

---

### Post by RockTeam on 2011-02-07
My problem has been resolved automatically since the last important system updates (xorg and etc.) was installed. Now hibernate function is working fine and I’ve not seen any low graphics mode warnings. Thanks to developers.

---

