---
title: "Gnome 3.2 working with compizconfig?"
date: 2012-03-10
forum: Desktop Environments
---

### Post by Spewed on 2012-03-10
Is there a way to get Gnome 3.2 working with Compizconfig? I can't seem to get that figured out.

---

### Post by 23dornot23d on 2012-03-10
Post the results of the following command .... type it in a terminal please


[B]
lspci[/B]


here is what it shows on mine as an example

> 
keith@keith-Aspire-7730ZG:~$ **lspci**
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
[COLOR=Red]**01:00.0 VGA compatible controller: NVIDIA Corporation G98 [GeForce 9300M GS] (rev a1)**[/COLOR]
06:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
06:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
06:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
06:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
07:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe (rev 10)
keith@keith-Aspire-7730ZG:~$ 

Reading the other threads you have posted - it seems to be you may not have your graphics set up for
acceleration .... ( this allows for the 3d and effects to work )

Once we determine the Graphics Card - and see if it is being used .... then we can see if compiz
will work ok .....


Also try this ....

[COLOR=Blue]**date && lsb_release -sd || cat  /etc/*release && uname -s -r && unity --version  && /usr/lib/nux/unity_support_test -p && dpkg -s  mesa-utils**[/COLOR]

> 
keith@keith-Aspire-7730ZG:~$ [COLOR=Blue]**date && lsb_release -sd || cat /etc/*release && uname -s -r && unity --version && /usr/lib/nux/unity_support_test -p && dpkg -s mesa-utils**[/COLOR]
Sat Mar 10 08:56:45 CET 2012
Linux Mint 12 LXDE
Linux 3.2.0-14-generic
unity 5.2.0
OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NV98
OpenGL version string:  2.1 Mesa 8.0-rc2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 132
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.0.1+git20110129+d8f7d6b-0ubuntu2
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Homepage: [http://mesa3d.sourceforge.net/](http://mesa3d.sourceforge.net/)
keith@keith-Aspire-7730ZG:~$ 



---

