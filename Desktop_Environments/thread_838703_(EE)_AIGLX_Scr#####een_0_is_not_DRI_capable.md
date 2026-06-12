---
title: "(EE) AIGLX: Scr#####een 0 is not DRI capable"
date: 2008-06-23
forum: Desktop Environments
---

### Post by eikichi on 2008-06-23
Hello, 

Recently I installed fluxbuntu (based on Ubuntu 7.10 x86) on an Acer satellite pro A120 with ATI RADEON XPRESS 200M graphics chip. Installation was complete and with no errors.

 I reboot and remove the CD, it takes me to the login page where I input my username and password, hit enter, the screen flashes, becomes black and takes back to the login page. 

I looked into my Xorg.0.log for critical errors and the only one I find was (EE) AIGLX: Screen 0 is not DRI capable.

cat /var/log/Xorg.0.log pipe grep EE returns me:

 (II) Loading extension MIT-SCREEN-SAVER
 (EE) AIGLX: Screen 0 is not DRI capable

Also from Xorg.0.log related to monitor and graphics chip

Section "Device"
   Identifier "ATI Technologies Inc RC410 [RADEON XPRESS 200M]"
   Driver     "ati"
   BusID      "PCI:1:5:0"
EndSection

Section "Monitor"
   Identifier "Generic Monitor"
   Option     "DPMS"
EndSection

Section "Default Screen"
   Identifier "Default Screen"
   Device "ATI Technologies Inc RC410 [RADEON XPRESS 200M]"
   Monitor    "Generic Monitor"
   Default Depth 24
   SubSection "Display"
             Mode      "1280x800"
EndSection

Rest of the sections are related with NIC, keyboard, touchpad etc..

I've googled the problem and got some threads reporting the same error but with no solution. Can someone provide a solution? obviously the problem lies on the graphics chip and/or the "ati" driver.

<edit>I tried chaging the driver from "ati" to "VESA" but it is not installed, also on grub i appended at the end of the kernel line vga=771 but with no avail.</edit>

---

