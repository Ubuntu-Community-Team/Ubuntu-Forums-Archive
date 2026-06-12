---
title: "Breezy Hangs; Feels Like an X or Driver Problem"
date: 2005-10-14
forum: Desktop Environments
---

### Post by dgoldssfo on 2005-10-14
Description of problem:
System is a dual-CPU Dell PowerEdge 1400SC, 1 GB RAM, ATI Mach 64 video on board.

I performed a fresh install of Breezy yesterday into an empty partition. After installation, my /etc/X11/xorg.conf file had the following: 

Section "Device"
        Identifier      "ATI Technologies, Inc. Rage XL"
        Driver          "ati"
        BusID           "PCI:0:14:0"
        VideoRam        65536
EndSection

When I run breezy, I experienced numerous system hangs. The system just locks up after anywhere from 15-60 minutes of use - various activities such as VPN, Firefox, Thunderbird, OpenOffice.org, etc. It does not seem to be recreatable or predicatble. Once it locks, I am unable to regain control other than via a reboot. I never experienced this problem with hoary running on the same computer.

 I did, however, experience exactly the same problem when I moved from Fedora Core 3 to Fedora Core 4 on the same computer. (See my bug report [https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=162702](https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=162702)) This problem is what got me over to Ubuntu in the first place. Now that I've gotten through the learning curve and really gotten to enjoy it, the same problem as with Fedora :mad: 

Another probably unrelated problem:

I noticed that the utility that puts together /etc/X11/xorg.conf got the amount of VideoRam on my card correct this time, unlike hoary. But Xorg is still not detecting the video RAM correctly. From /var/X11/Xorg.0.log:

(--) ATI(0): 4096 kB of SGRAM (2:1) 32-bit detected (using 4095 kB).

I have seen this problem mentioned by another user on Google but would love a workaround or solution.

Questions:

1. Is there any way to get around the system hang once it happens, short of rebooting? Cntl_Alt_Backspace leaves me with a blank screen and X will not restart.

2. Is there a workaround for this problem so that it never happens? 

3. Does anyone know how to get Xorg to recognize that this card has 64MB instead of 4 MB?

Thanks!

---

