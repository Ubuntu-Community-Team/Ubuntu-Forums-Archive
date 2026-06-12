---
title: "newbie need help with debian+touch screen"
date: 2008-04-09
forum: Debian
---

### Post by shahin123 on 2008-04-09
Hi,

I have a problem with installing the Elo touch,

I did install the elo touch with this:
aptitude install xserver-xorg-input-elographics


then opened /etc/X11/xorg.conf and there I did add these, (in this file I could see 2 sectios that start with Section "InputDevice" so I add mine after the secound one)

Section "InputDevice"
Identifier "Touchscreen"
Driver "elographics"
Option "screenno" "0" 
Option "ButtonNumber" "1" 
Option "ButtonThreshold" "17"
Option "Device" "/dev/ttyS1"
Option "InputFashion" "Touchpanel"
Option "MaxX" "4025"
Option "MinX" "22"
Option "MaxY" "3967" 
Option "MinY" "75"
Option "Name" "ELO Touchscreen"
Option "ReportingMode" "Scaled"
Option "SendCoreEvents" "on"
EndSection
and I also add next line in 
"ServerLayout"

InputDevice "Touchscreen" "SendCoreEvents"
but after rebooting the system the system I have still no touch 
I have debian etch on my box

Any idea how to sole this issue?

Thanks,

Shahin

---

### Post by patrick9999 on 2008-05-29
try: cat /dev/ttyS1 and click on screen, else try cat /dev/ttyS0

and modify in your xorg.conf

i have problem too, calibration is "inversed, when i move finger up, pointer go down ... and inverse

but it is correct for left and right ? any idea ? 

i have the same xorg.conf as shahin123

---

### Post by Sef on 2008-05-29
Moved to the Debian Forum.

---

### Post by tbb9216 on 2009-01-22
> **patrick9999 said:**
> try: cat /dev/ttyS1 and click on screen, else try cat /dev/ttyS0

and modify in your xorg.conf

i have problem too, calibration is "inversed, when i move finger up, pointer go down ... and inverse

but it is correct for left and right ? any idea ? 

i have the same xorg.conf as shahin123

i know its been a few months since you posted this, but incase you havent figured it out, you can add the options of swapx and swapy

Option "SwapX" "true"
Option "SwapY" "true"

or, of course you could just swap them in your actual config, eg: change MinX=1 MaxX=2 to MinX=2 MaxX=1

hopefully thatll help you out.

-tim

---

### Post by tbb9216 on 2009-01-22
> **shahin123 said:**
> Hi,

I have a problem with installing the Elo touch,

I did install the elo touch with this:
aptitude install xserver-xorg-input-elographics


then opened /etc/X11/xorg.conf and there I did add these, (in this file I could see 2 sectios that start with Section "InputDevice" so I add mine after the secound one)

Section "InputDevice"
Identifier "Touchscreen"
Driver "elographics"
Option "screenno" "0" 
Option "ButtonNumber" "1" 
Option "ButtonThreshold" "17"
Option "Device" "/dev/ttyS1"
Option "InputFashion" "Touchpanel"
Option "MaxX" "4025"
Option "MinX" "22"
Option "MaxY" "3967" 
Option "MinY" "75"
Option "Name" "ELO Touchscreen"
Option "ReportingMode" "Scaled"
Option "SendCoreEvents" "on"
EndSection
and I also add next line in 
"ServerLayout"

InputDevice "Touchscreen" "SendCoreEvents"
but after rebooting the system the system I have still no touch 
I have debian etch on my box

Any idea how to sole this issue?

Thanks,

Shahin

if you havent had success yet, have you tried the evtouch drivers?  those are what i use for my system that has to auto-install, so i cant calibrate every unit individually and im not smart enough to build the correct drivers myself to install easily.  so they dont take advantage of the greater technology of the elo units, but it works for what i need

-tim

---

