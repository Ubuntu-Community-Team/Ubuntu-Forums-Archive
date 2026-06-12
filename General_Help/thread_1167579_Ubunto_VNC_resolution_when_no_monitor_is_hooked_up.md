---
title: "Ubunto VNC resolution when no monitor is hooked up."
date: 2009-05-23
forum: General Help
---

### Post by Jabcor on 2009-05-23
Hello

When I have a monitor connected to my Ubuntu box, my resolution is fine when I use VNC.  Even if I unhook it, it remains fine.  However, when I reboot, the resolution when using VNC becomes very small.

Is there a configuration somewhere that I can set it to be a default regardless if I boot with a monitor or not?

---

### Post by CatKiller on 2009-05-23
When it's available, EDID is used by X to let it automatically set the correct refresh rate. When EDID is not available, X defaults to really low values that won't damage any monitors. If you give X the values that it needs to automatically configure the display for your monitor, it doesn't matter if the monitor is plugged in or not.

You can manually set the values for your monitor by putting the VertRefresh and HorizSync ranges in your xorg.conf. You should be able to get these numbers from a X's log (/var/log/Xorg.0.log) when you've booted the computer with the monitor plugged in. These values go in the "Monitor" Section of xorg.conf, like so:
```
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       aa-bb
        VertRefresh     cc-dd
EndSection

```You may also need to put 
```
        Option          "UseEDID"                       "False"
```in the "Device" Section.

---

### Post by Jabcor on 2009-05-23
Thanks, CatKiller.

What is it I'm looking for in the log file?  I could not find that anything that referenced HorizSync or VertRefresh in the log.  I do see "System resource ranges", but i'm not if that is what I'm looking for:

```
(--) PCI:*(0@1:0:0) nVidia Corporation NV34 [GeForce FX 5200] rev 161, Mem @ 0xf2000000/16777216, 0xe0000000/268435456, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [5] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [6] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [7] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [8] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [9] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [10] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [11] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [12] -1 0       0xffffffff - 0xffffffff (0x1) MX[B]
        [13] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [14] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [15] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [16] -1 0       0xffffffff - 0xffffffff (0x1) MX[B]
        [17] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [18] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [19] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [20] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [21] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]
        [22] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [23] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]
        [24] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [25] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]
        [26] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [27] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]
        [28] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [29] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]

```

---

### Post by CatKiller on 2009-05-23
You can make a copy of the file on your Desktop with ```
cat /var/log/Xorg.0.log > ~/Desktop/Xorg.log
``` There should be a bunch of stuff in there about the EDID values that it's received from the monitor and then more stuff about setting modes. Otherwise, you could just get the values you need from your monitor's manual.

---

