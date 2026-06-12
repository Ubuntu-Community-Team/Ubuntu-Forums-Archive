---
title: "KDE hangs after FGLRX upgrade"
date: 2010-03-06
forum: Desktop Environments
---

### Post by unauthorized on 2010-03-06
Hello Ubuntu community,
I recently decided to upgrade my video card driver to the latest vendor distributed version. Right after the upgrade, KDE stopped working. Every time I tried to start a session, it would always get stuck on the "loading" animation right after the disk icon appears. In this state, it's possible to switch in another tty session, but the desktop environment doesn't load, or at least not within less than an hour.

It's still possible to login into other sessions (at least to GNOME and console) just fine and I'm sure the video driver works correctly (it runs heavy 3D accelerated apps fine), but nothing I could think of will make KDE run.

The funny thing is that it used to work fine with the FGLRX driver supplied with Ubuntu. After the upgrade, I tried to remove the driver and apt-get the Ubuntu supplied driver package, but it wouldn't enable in the "Hardware Drivers" utility and setting flgrx in xorg.conf would cause the system to boot into low resolution mode (not sure of the exact name). The only solution to recover from that is to completely uninstall the driver package and manually set the open source "radeon" driver. 

I tried to "mv ~/.kde", "genkdmconf --no-old" and even booting without xorg.conf but neither helped.

Here's the kdm boot log entry for my last attempt: 
> 
X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server x86_64 Ubuntu
Current Operating System: Linux spambot 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:02:26 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-generic root=UUID=cbbca94a-a535-450e-8b73-cb406038c59b ro quiet splash
Build Date: 14 November 2009  05:48:57PM
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@) 
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Mar  6 18:57:42 2010
(==) Using config file: "/etc/X11/xorg.conf"
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found


---

### Post by aarons6 on 2010-03-07
heres what probably happened.. you had desk effects enabled..
your openglcore libs were symlinked to the fglrx drivers, when you uninstalled the installer deleted the links but kept the files.. 

try to reinstall the opengl libs.
libgl1-mesa-glx


ignore this
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found 			 		

that is the hdmi sound..

---

### Post by Melcar on 2010-03-07
The latest driver has issues with composition.  Turn it off and you should be fine, or downgrade to the 10.1 driver.

---

