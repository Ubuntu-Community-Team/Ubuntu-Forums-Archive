---
title: "gdm or/and Xorg fails and cannot restart themselves"
date: 2009-01-30
forum: General Help
---

### Post by rnr4ever on 2009-01-30
Hi everyone,

I have recently installed Ubuntu on a desktop I pieced together from various free parts from Craigslist. It boots fine and runs fine until gdm/Xorg fails. I tried googling for a fix...but couldn't find anything of help. Below is a log that I saved:

> 
5626 4718
xinit /etc/gdm/failsafeXinit /etc/X11/xorg.conf.failsafe with-gdm -- /usr/bin/X :0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7 -br -once -config /etc/X11/xorg.conf.failsafe -logfile /var/log/Xorg.failsafe.log

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux starburst 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(++) Log file: "/var/log/Xorg.failsafe.log", Time: Fri Jan 16 12:57:28 2009
(++) Using config file: "/etc/X11/xorg.conf.failsafe"

error setting MTRR (base = 0xf0000000, size = 0x000d0000, type = 1) Invalid argument (22)
5626 4718


Below is from lshw, in case anyone wants to know about my salvaged hardware:

> 
starburst
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1515MiB
     *-cpu
          product: Intel(R) Pentium(R) 4 CPU 1500MHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.0.10
          size: 1500MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up pebs bts
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 8KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 256KiB
     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display UNCLAIMED
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
           *-network
                description: Ethernet interface
                product: 82801DB PRO/100 VE (LOM) Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:01:08.0
                logical name: eth1
                version: 81
                serial: 00:0c:f1:c9:a3:84
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=192.168.1.100 latency=32 maxlatency=56 mingnt=8 module=e100 multicast=yes
        *-isa
             description: ISA bridge
             product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DB (ICH4) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0 module=ata_piix
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 7c:4c:4c:35:5c:18
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


Any help would be much appreciated by a financially-challenged college student, thanks.

-rnr

---

### Post by Yashiro on 2009-01-30
Which Ubuntu version and are you able to run from the LiveCD (Test wthout installing to HD)?

---

### Post by rnr4ever on 2009-01-30
I am running Ubuntu 8.10, and LiveCD works fine as far as I know. I think it's a good idea to run solely on LiveCD for a day to see what happens. Thanks for the suggestion.

---

### Post by PmDematagoda on 2009-01-30
Can you post the contents of the /etc/X11/xorg.conf file?

---

### Post by khedron on 2009-01-30
If your /etc/X11/xorg.conf file is OK, I think you could look into the **nomtrr** option in /etc/X11/xorg.conf to disable mtrr completely in X. That might help.

---

### Post by rnr4ever on 2009-01-30
> **khedron said:**
> If your /etc/X11/xorg.conf file is OK, I think you could look into the **nomtrr** option in /etc/X11/xorg.conf to disable mtrr completely in X. That might help.

I wanted to test things out in my xorg.conf, but I read that if I do anything wrong, I won't be able to boot. I tried doing the dpkg-reconfigure xserver-xorg, but same problem persists.

> **PmDematagoda said:**
> Can you post the contents of the /etc/X11/xorg.conf file?

Sure. Below is my xorg.conf (after doing dpkg-reconfigure xserver-xorg):

> 
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
    Identifier    "Configured Video Device"
  Driver      "intel"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection


---

### Post by khedron on 2009-01-31
If you do decide to change your xorg.conf, there is a not-too-hard way to rescue the system.

You can try it now. **Ctrl-Alt-F7** is your graphical session, and **Ctrl-Alt-F1** is a "Virtual Console". If you change your xorg.conf and X doesn't load, you will be dropped onto a Virtual Console. You can edit your xorg.conf while there by logging in and typing ```
sudo nano /etc/X11/xorg.conf
```Then you can type **startx** to try to restart X. If that fails, just reedit xorg.conf with the above command, or run ```
sudo dpkg-reconfigure xserver-xorg
startx
```I have messed up my xorg.conf quite a few times and found it fine. Just check that the Virtual Console is useable. In some rare cases, it might not be. Press **Ctrl-Alt-F1** to test it now, and press **Ctrl-Alt-F7** to get back to the GUI.

---

### Post by IsmailBhai on 2009-03-06
i was having this same error setting mtrr problem.  follow this guide, it might help.

[http://hydtechblog.com/2009/02/26/gnome-display-manager-problems-error-setting-mtrr-in-ubuntu-intrepid-810/]("http://hydtechblog.com/2009/02/26/gnome-display-manager-problems-error-setting-mtrr-in-ubuntu-intrepid-810/")

---

