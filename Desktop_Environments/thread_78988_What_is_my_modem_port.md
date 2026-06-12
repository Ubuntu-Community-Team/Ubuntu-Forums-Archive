---
title: "What is my modem port?"
date: 2005-10-19
forum: Desktop Environments
---

### Post by BRODEL on 2005-10-19
I am trying to setup a dialup connection and it's asking for the modem port. I'm not sure what it is and Autodetect didn't work. I do see the modem in device manager, but I don't see anything about what port it's on. 

This is on a Toshiba laptop if that matters. Thanks.

---

### Post by yage on 2005-10-19
Try this 
```
lspci
```
and see if the modem was detected.
It's been a long time since i used a modem with linux but i think the port was linked to /dev/modem

---

### Post by hajk on 2005-10-19
You could try /dev/ttyS0 or /dev/ttyS1 (if it is a serial port) -- it is also possible that /dev/modem is already a symlink to either one.

---

### Post by BRODEL on 2005-10-19
Ok, here is the output from the lspci command

> 0000:00:00.0 Host bridge: Intel Corp. 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
0000:00:01.0 PCI bridge: Intel Corp. 82845 845 (Brookdale) Chipset AGP Bridge (r ev 04)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 05)
0000:00:1f.0 ISA bridge: Intel Corp. 82801BA ISA Bridge (LPC) (rev 05)
0000:00:1f.1 IDE interface: Intel Corp. 82801BA IDE U100 (rev 05)
0000:00:1f.2 USB Controller: Intel Corp. 82801BA/BAM USB (Hub #1) (rev 05)
0000:00:1f.3 SMBus: Intel Corp. 82801BA/BAM SMBus (rev 05)
0000:00:1f.4 USB Controller: Intel Corp. 82801BA/BAM USB (Hub #2) (rev 05)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801BA/BAM AC'97 Audio (r ev 05)
**0000:00:1f.6 Modem: Intel Corp. Intel 537 [82801BA/BAM AC'97 Modem] (rev 05)**
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
0000:02:00.0 CardBus bridge: O2 Micro, Inc. OZ6933 Cardbus Controller (rev 01)
0000:02:00.1 CardBus bridge: O2 Micro, Inc. OZ6933 Cardbus Controller (rev 01)
0000:02:08.0 Ethernet controller: Intel Corp. 82801BA/BAM/CA/CAM Ethernet Contro ller (rev 03)
0000:02:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000  Controller (PHY/Link)


I bolded what I think the modem is. Does the "0000:00:1f.6" mean anything? 

Thanks.

---

### Post by BRODEL on 2005-10-19
Ok. I set it to /dev/modem but when I go back and click Activate on the modem connection, it says 

"Could not enable the interface ppp0
Check that the settings are correct for this network and that the computer is correctly connected to it."

---

### Post by migueljacq on 2005-10-19
[QUOTE=BRODEL]Ok. I set it to /dev/modem but when I go back and click Activate on the modem connection, it says 

"Could not enable the interface ppp0
Check that the settings are correct for this network and that the computer is correctly connected to it."[/QUOTE]

Is it an internal winmodem?

Have you run 'sudo pppconfig' from the terminal and configured the modem dial-out details?

for pppconfig steps, I wrote in this thread:

[http://ubuntuforums.org/showthread.php?p=419217](http://ubuntuforums.org/showthread.php?p=419217)

(love the Jayne pic by the way :-))

---

