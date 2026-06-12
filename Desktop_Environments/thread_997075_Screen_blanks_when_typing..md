---
title: "Screen blanks when typing."
date: 2008-11-29
forum: Desktop Environments
---

### Post by JimGvo on 2008-11-29
I just installed Kubuntu 8.10 on a system.  Something is managing my display/video card and keyboard and it's NOT xorg.conf.  

When I type a key, I see a brief flash about one line high across the screen in random places.  If I type too fast the screen blanks out for about 3 seconds.  It also will blank out once in a while if I'm not typing fast.  The system is not halting, since if I keep typing while the screen is blanked, it appears on the screen when it comes back.  The screen has blanked out about 35 times during the typing of this message.  

The keyboard is plugged into the ps2 slot.  The video card is onboard the ASUS motherboard:

01:03.0 VGA compatible controller: XGI Technology Inc. (eXtreme Graphics Innovation) Volari Z7/Z9/Z9s
        Subsystem: ASUSTeK Computer Inc. Device 823d
        Flags: 66MHz, medium devsel
        BIST result: 00
        Memory at fc000000 (32-bit, prefetchable) [size=32M]
        Memory at ff7c0000 (32-bit, non-prefetchable) [size=256K]
        I/O ports at dc00 [size=128]
        Capabilities: <access denied>
        Kernel modules: sisfb

The driver is "sys" in xorg.conf.  

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "sis"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

The monitor is a Hanns-G HW173D

Mouse actiity has no similar effect on the display.  Nothing in any log in /var/log during the failure times.

Linux version 2.6.27-7-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu10) ) #1 SMP Fri Oct 24 06:42:44 UTC 2008 (Ubuntu 2.6.27-7.14-generic)
 
ASUS P5M2-M/RS-100-E4 Motherboard

Any suggestions? 

Thanks,
Jim

---

### Post by betnexrel on 2008-11-30
Have you tried to disable spell checking? (when you type in kde applications)

---

### Post by JimGvo on 2008-12-01
No but it isn't always a KDE app that causes the problem.  It's all applications include a terminal window, Firefox, games, etc.  This is a fairly fast 2 core system with 2 Gb of memory and a SATA drive.  Somehow I can't think an app like a spell checker would have any effect.  

Jim.

---

