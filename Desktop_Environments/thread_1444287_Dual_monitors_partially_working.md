---
title: "Dual monitors partially working"
date: 2010-04-01
forum: Desktop Environments
---

### Post by seanmsiegel on 2010-04-01
Im fairly new to linux and have tried all that i can think of at this point. Hopefully i provided enough details and someone out there knowns whats going on :)

I have intel onboard video and an pci-e ati x300 card. With my onboard video controller set as the primary graphics device in bios(yes the pci-e is still enabled but is just not set as the primary controller), I did a clean installation of ubuntu 9.10 and ubuntu seems to only detect one monitor. I goto system>prefs>display and there is only 1 display listed.

I then returned to bios and switched the primary graphics controller to my pci-e card and then booted into ubuntu. I still only have on monitor but now the pci-e is working and the onboard is not. I still only have one display in system>prefs>display

A quick peek at /var/log/Xorg.0.log shows that both controllers seem to be being detected as far as i know:
(--) PCI:*(0:0:2:0) 8086:29c2:1458:d000 Intel Corporation 82G33/G31 Express Integrated Graphics Controller rev 16, Mem @ 0xeb200000/524288, 0xd0000000/268435456, 0xeb000000/1048576, I/O @ 0x0000e000/8
(--) PCI: (0:1:0:0) 1002:5b60:174b:0500 ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)] rev 0, Mem @ 0xe0000000/134217728, 0xe9000000/65536, I/O @ 0x0000c000/256, BIOS @ 0x????????/131072

I then decided to generate two seperate xorg.conf files, one for each controller. so i ran Xorg -configure which created /root/xorg.conf.new. I copied this file to xorg.conf.ati and then switched back the primary controller to my intel onboard and repeated the process renaming the second file as xorg.conf.intel (both of these files have been attached). Looking at both files, they both have both the intel and ati device listed and two screens. The only difference is that both config files only had 1 monitor configured. One of them had monitor0 configured and the other only had monitor1 configured. This being the ONLY difference in the files, i decided to just copy the settings from monitor0 to monitor1 so the my config now has two monitors (both monitors are identical makes and models anyways). (i attached my custom xorg.conf file as xorg.conf.custom. When testing each config file, i did copy them to /etc/X11/xorg.conf, rebooted, and /var/log/Xorg.0.log did report loading the file.

I then rebooted and now see to have SOME progress! :). I now have my active monitor with my desktop and the second monitor is displaying the longon screens background image (the spotlight shining down onto the stage). I can move my mouse over to this monitor but cannot drag anything to it. When i drag a window to the edge of my active monitor, it rolls over to the next virtual desktop or panel..

Even with an image on both monitors and partial functionality, i still only have 1 display in /system/prefs/display

Does anyone has any ideas?

I have also attached my Xorg.0.log file generated when booting to my custome xorg.conf file. I do notice 1 error in the file (search for '(EE)') referring to my ati video adapter. I dont believe this is the issue or even a major issue as i have video on the monitor attached, i just cannot drag windows onto the monitor.


Thanks in advance!

---

