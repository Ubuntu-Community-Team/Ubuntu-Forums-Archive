---
title: "no auto monitor detection??"
date: 2005-09-10
forum: Desktop Environments
---

### Post by X5-655 on 2005-09-10
why doesn't Ubuntu automatically detect the refresh rates of a monitor?  I am seeing that it has to be manually done...

---

### Post by Leif on 2005-09-10
afaik, because monitors don't identify themselves properly. it is another instance of hardware manufacturers not supporting linux.

---

### Post by X5-655 on 2005-09-10
[QUOTE=Leif]afaik, because monitors don't identify themselves properly. it is another instance of hardware manufacturers not supporting linux.[/QUOTE]
actually, monitors all support DDC, which is part of the VESA standard, which allows a monitor to tell the operating system what resolution, scan rates, and refresh rates it supports.

if Ubuntu was to read the DDC, it could very much help.

This isn't a windows feature, or anything not supporting linux.  since it is a setup VESA standard, Linux should support it, and matter of fact, I think Mandrake does...

---

### Post by X5-655 on 2005-09-10
[QUOTE=Leif]afaik, because monitors don't identify themselves properly. it is another instance of hardware manufacturers not supporting linux.[/QUOTE]
for example, here's my monitors DDC information..  straight from the DDC line on my monitors VGA cable..  surely Linux should understand this...

(08-09)  ID Manufacturer Name ________________  = GWY
(11-10)  Product ID Code _____________________  = 02D0(Ð)
(12-15)  Last 5 Digits of Serial Number ______  = (Removed)
(16)     Week of Manufacture _________________  = 34
(17)     Year of Manufacture _________________  = 2000
(10-17)  Complete Serial Number ______________  = (Removed)
(18)     EDID Version Number _________________  = 1
(19)     EDID Revision Number ________________  = 1
(20)     VIDEO INPUT DEFINITION:
         Analog Signal
         0.700, 0.300 (1.000 Vp-p)
         Separate Syncs, Composite Sync
(21)     Maximum Horizontal Image Size ________________    =  310 mm
(22)     Maximum Vertical Image Size __________________    =  230 mm
(23)     Display Gamma ________________________________    =  2.63
(24)     Power Management and Supported Feature(s):
         Stand-By, Suspend, Active Off/Very Low Power
         Display Type = R/G/B Color
(25-34)  CHROMA INFO:
         Red X - 0.626 Green X - 0.278 Blue X - 0.150 White X - 0.281
         Red Y - 0.338 Green Y - 0.601 Blue Y - 0.068 White Y - 0.311
(35)     ESTABLISHED TIMING I:
         720 X 400 @ 70Hz (IBM,VGA)
         720 X 400 @ 88Hz (IBM,XGA2)
         640 X 480 @ 60Hz (IBM,VGA)
         640 X 480 @ 67Hz (Apple,Mac II)
         640 X 480 @ 72Hz (VESA)
         640 X 480 @ 75Hz (VESA)
         800 X 600 @ 56Hz (VESA)
         800 X 600 @ 60Hz (VESA)
(36)     ESTABLISHED TIMING II:
         800 X 600 @ 72Hz (VESA)
         800 X 600 @ 75Hz (VESA)
         832 X 624 @ 75Hz (Apple,Mac II)
         1024 X 768 @ 60Hz (VESA)
         1024 X 768 @ 70Hz (VESA)
         1024 X 768 @ 75Hz (VESA)
         1280 X 1024 @ 75Hz (VESA)
(37)     Manufacturer's Reserved Timing:
         1152 X 870 @ 75Hz (Apple,Mac II)
(38-53)  Standard Timing Identification:
         1600 X 1200 @70Hz
         1600 X 1200 @60Hz
         1280 X 1024 @85Hz
         1280 X 960 @85Hz
         1152 X 864 @75Hz
         1024 X 768 @85Hz
         800 X 600 @85Hz
         640 X 480 @85Hz
______________________________________________________________________
(54-71) Detailed Timing / Descriptor Block 1:
                  1600x1200  Pixel Clock: 202.50 MHz
______________________________________________________________________
         Horizontal Image Size: 317 mm     Vertical Image Size: 236 mm
         Refreshed Mode: Non-Interlaced    Normal Display - No Stereo

Horizontal:
         Active Time: 1600 pixels          Blanking Time: 560 pixels
         Sync Offset: 64 pixels            Sync Pulse Width: 192 pixels
         Border: 0 pixels                  Frequency: 93.75 KHz

Vertical:
         Active Time: 1200 lines           Blanking Time: 50 lines
         Sync Offset: 1 lines              Sync Pulse Width: 3 lines
         Border: 0 lines                   Frequency: 75.00 Hz

Digital Separate, Horizontal Polarity (+) Vertical Polarity (+)


______________________________________________________________________
(72-89) Detailed Timing / Descriptor Block 2:

         Monitor Range Limits:
         Min Vertical Freq - 50 Hz
         Max Vertical Freq - 130 Hz
         Min Horiz. Freq - 30 KHz
         Max Horiz. Freq - 96 KHz
         Pixel Clock  - 220 MHz
         Secondary GTF - Not Supported

______________________________________________________________________
(90-107) Detailed Timing / Descriptor Block 3:

         Monitor Name:
         VX720


______________________________________________________________________
(108-125) Detailed Timing / Descriptor Block 4:

         Monitor Serial Number:
         (Removed)


(126)    No Extension EDID Block(s)
(127)    CheckSum OK

---

