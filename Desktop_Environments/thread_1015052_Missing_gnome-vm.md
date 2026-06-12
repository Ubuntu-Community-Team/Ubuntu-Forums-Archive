---
title: "Missing gnome-vm"
date: 2008-12-18
forum: Desktop Environments
---

### Post by berkshire779 on 2008-12-18
I installed Ubuntu 8.10 on a Compaq EVO D51S.  After logging into the GUI login screen.  The screen goes blank with only an active mouse cursor.  I came across the following error file:

cat .xsession-errors
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for local=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /eetc/X11/xinit/xinput.d/default.
gnome-session[5007]:WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanger'
Checking for Xgl: not present.
Detected PCI ID for VGA:
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1152x864) to maximum 3D testure size (2048): Passed
Checking for nVidia: not present.
Checking for FBConfig; present.
Checking for Xgl: not present.
gnome-session[5007]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout

  I am assuming that the failure of gnome virtual machine to intialize is the problem.  I have tried two different downloads of Ubunto 8.10 to no avail.  Any suggestions?  Please be specific as I am new to this OS.  Thanks for your time.

---

### Post by berkshire779 on 2008-12-19
The .xsession-errors listed above resulted from a conflict with the chip set in the Compaq EVO D51S (thanks Moonmind @ Linux Questions Forum).  See chipset list below.  To get around this problem I installed a graphics card in the PCI bus and rebooted the computer.  Ubuntu loaded correctly into the desktop and I used update manager to download updates.  I shut the computer down and removed the newly installed graphics card, restarted the computer and Ubuntu is operating correctly.  The updates appear to have corrected the problem.  

 lspci

00:00.0 Host bridge: Intel Corporation 82845G/GL{Brookdale-G]/GE/PE DRAM controller/Host Interface (rev01)

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Intergated Graphics Device (rev01)

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev01)

00:1d.1	USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev01)

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev01)

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev81)

00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev01)

00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M SMBus Controller (rev 01)

00:1f.5 Multimedia audio controller:  Intel Corporation 82801DB/DBL/DBM (ICH4/ICH5-L/ICH4-M) AC'97 Audio Controller (rev 01)

05:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VM (LOM) Ethernet Controller (rev 81)

---

