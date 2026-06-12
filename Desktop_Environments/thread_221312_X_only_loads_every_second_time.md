---
title: "X only loads every second time"
date: 2006-07-22
forum: Desktop Environments
---

### Post by perky on 2006-07-22
Almost every boot, X fails(?) to load and am faced with a black screen.  The login sound still plays.  Resetting fixes the problem, but I don't want to have to boot my computer twice every time I want to use!

Video card is an S3 86C270-294 Savage/IX-MV.
Laptop is an IBM Thinkpad T21.

Please help!

---

### Post by st00ner on 2006-07-22
try reconfiguring X, i believe there is a thread on the forums with how to do that

---

### Post by perky on 2006-07-22
> **st00ner said:**
> try reconfiguring X, i believe there is a thread on the forums with how to do that

Just tried, same problem still :/

Any other ideas?

---

### Post by yurtboy on 2006-08-09
I have the same problem on a t20 and t22 on three different machines.
I am looking for acpi settings or something to fix it.
It just boots to a black screen with a cursor on the top left hand corner.

---

### Post by The Road Below on 2006-08-11
Same prob on t22.  Switched to xubuntu.  Smooth, including kernel upgrade.

---

### Post by isharra on 2006-08-12
I used to have this problem. apologies for what is turning out to be a much longer post than I'd intended. Hopefully it will be of help to someone.

Power management settings get confusing since the bios date determines if by default you use apm (before 2000) or acpi. I installed ubuntu on my t22 (2002 bios) so I could help talk my kid through troubles with the t20 (1998 bios). For consistency I ended up using these additions to the kernel options line (# kopt) "ec_intr=0 floppy=thinkpad acpi noapm". Don't forget to 'upgrade-grub' after making changes to /boot/grub/menu.lst.

ec_intr=0 was needed for kernels 2.6.15-25/26 in order to power off the t22. I don't see this mentioned much in these forums so perhaps I'm just unlucky. Suspend and hibernate do not work for me with these ubuntu kernels, you may want to hold your linux-image to 2.6.15-23. The edgy kernel 2.6.17-4 will hibernate but not suspend. (I tried edgy installs for xubuntu and ubuntu but dropped back to dapper.) Custom kernels compiled from kernel.org source of 2.6.17.8 and 2.8.18-rc4 do suspend and hibernate properly. 

Changes to xorg.conf did work for me. I'm copying my changes below just in case they don't match what you tried.

(Note: 16 bit color depth is needed for 3d accelleration. 24 bit at 1024x768 requires more than the 8 meg of memory that is supplied for the video. As a side effect video playback became smoother as well. If you're lucky enough to have the 1400x1050 screen: the mode lines need to be changed and the horizontal frequency may need to be increased as well.)

```
Section "Device"
        Identifier      "S3 Inc. 86C270-294 Savage/IX-MV"
        Driver          "savage"
        BusID           "PCI:1:0:0"
        VideoRam        8192
        Option          "DmaMode"               "None"
        Option          "BusType"               "PCI"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        Option          "NoDDC"
        HorizSync       31.5-48.5
        VertRefresh     50-90
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "S3 Inc. 86C270-294 Savage/IX-MV"
        Monitor         "Generic Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection
```

---

### Post by paulvbrown on 2006-08-18
I swear this is the same problem I was having -- answered it here:

[http://www.ubuntuforums.org/showthread.php?t=225588](http://www.ubuntuforums.org/showthread.php?t=225588)

-paul

---

