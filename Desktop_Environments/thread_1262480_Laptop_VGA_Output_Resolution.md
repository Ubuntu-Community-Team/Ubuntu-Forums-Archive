---
title: "Laptop VGA Output Resolution"
date: 2009-09-09
forum: Desktop Environments
---

### Post by c00lryguy on 2009-09-09
Hello all, I just reinstalled Ubuntu with 9.04 on my (crappy) laptop coming from 8.04. I have the laptop connected with a VGA output on the laptop to my flat screen monitor, which turns off the laptop screen.

Everything runs great, it's just the maximum resolution only goes up to 800x600. On 8.04 I was able to set it to 1024×768 (which is still too big for me, but it was better than 800x600). 

I ran xrandr and this is the output it gives me:
```
ryguy@ryguy-laptop:~$ xrandr
Screen 0: minimum 320 x 240, current 800 x 600, maximum 800 x 600
```Is there anyway I can set it to 1024x768, or even better would be 1280x1024? I know the monitor is capable of such resolutions.

**Laptop information:**
  Toshiba Tecra 8200.  On the bottom it says: 
  P850,14,256,10,C.M/L 
PART NO. PT820U-01DSGB

---

### Post by mariusc on 2009-09-09
Hi,
How your /etc/X11/xorg.conf looks ? Paste it here ?

Or try:
backup your current xorg.conf first because in  Linux everything is impredictible.

$>sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bkp 

make the teminal window larger (size it) approx 150% 
run 'gtf H-rez-pix V-rez-pix Freq' 

$>gtf 1024 768 50

copy the response of above command
open xorg.conf in root mode

Copy the Modeline line in the Monitor section

[COLOR="Blue"] Section "Monitor"
       Identifier  "Configured Monitor"
       # paste mode line here
       # paste another mode line here
 EndSection
[/COLOR]

add the modes here too

SubSection "Display"
             ...
              Modes "1360x768"  "1280x1024" <"other modes">     
              Virtual 1280 1024 # max of all Hs and Vs from modes
EndSubSection


restart







$>gtf 1024 768 60

---

### Post by c00lryguy on 2009-09-09
```
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```

---

### Post by mariusc on 2009-09-09
Or try:
backup your current xorg.conf first because in Linux everything is impredictible.

[PHP]$>sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bkp[/PHP]

make the teminal window larger (size it) approx 150%
[PHP]run 'gtf H-rez-pix V-rez-pix Freq'[/PHP]

[PHP]$>gtf 1024 768 50[/PHP]

copy the response of above command
open xorg.conf in root mode

Copy the Modeline line in the Monitor section
[PHP]
Section "Monitor"
Identifier "Configured Monitor"
# paste mode line here
# paste another mode line here
EndSection[/PHP]

sample:
[PHP]
Section "Monitor"
       Identifier  "Configured Monitor"
       Modeline "1360x768_60.00"  84.72  1360 1424 1568 1776  768 769 772 795  -HSync +Vsync
       # other modeline
 EndSection
[/PHP]

add the modes here too

On your Section &#8220;Screen&#8221; add the following before the EndSection

[PHP]

SubSection "Display"
   ...
   Modes "1360x768" "1280x1024" <"other modes">
   Virtual 1360 1024 # max of all Hs and Vs from modes
EndSubSection[/PHP]


to look

[PHP]Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    SubSection "Display"
        Modes "1360x768" "1280x1024" <"other modes">
        Virtual 1360 1024 # max of all Hs and Vs from modes
    EndSubSection
EndSection[/PHP]


restart .... check the display settings again. 
Please let me know if worked.

---

### Post by c00lryguy on 2009-09-09
I'm a tad but confused about the SubSection "Display" part of your example.

Please explain the "Virtual" part more clearly? What do you mean by max of all the Hs and Vs modes?[COLOR=#000000][COLOR=#0000bb]
[COLOR=Black]
Here's what I have so far:

[/COLOR][/COLOR][/COLOR][php]
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    Modeline "1024x768_50.00"  51.89  1024 1064 1168 1312  768 769 772 791  -HSync +Vsync
    Modeline "1280x1024_50.00"  89.38  1280 1352 1488 1696  1024 1025 1028 1054  -HSync +Vsync
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"

    SubSection "Display"
        Modes "1024x768" "1280x1024"
        Virtual 1360 1024 # max of all Hs and Vs from modes
    EndSubSection
EndSection[/php]

---

### Post by mariusc on 2009-09-10
Hi,
Your conf. looks ok , except virtual but it should work.

I am not sure but I think this is how it goes

[PHP]your res. are: h=1024 v=768
               h=1280 v=1024
           max(1024, 1280) = 1280    
           max(768, 1024)  = 1024[/PHP]

so virtual has 1280 1024 

[PHP] SubSection "Display"
        Modes "1024x768" "1280x1024"
        Virtual 1280 1024 # should work. 
 EndSubSection[/PHP]


They dont say to much about virtual:

[http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html](http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html)

---

### Post by c00lryguy on 2009-09-10
hey, I just sent you a PM. I'm going to try to remove the "[COLOR=#000000][COLOR=#DD0000]1280x1024[COLOR=Black]" lines[/COLOR]
[/COLOR][/COLOR]

---

### Post by mariusc on 2009-09-10
Hi,

So... I was wrong with the virtual. Remove ot . They say v-size will auto-adjust 
from the modelines if the virtual line is missing. 
If does not work make it as the resolution.

---

### Post by c00lryguy on 2009-09-10
Yeah, I changed it to 1024x768 and I still have the screen-scroll problem. I'm going to remove the "virtual" line like you said and restart and report back to ya. Thanks for all your help, btw. =)

---

### Post by c00lryguy on 2009-09-10
Okay, now 1024x768 isn't displaying at all with these settings:
[PHP]Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    Modeline "1024x768_50.00"  51.89  1024 1064 1168 1312  768 769 772 791  -HSync +Vsync
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"

    SubSection "Display"
        Modes "1024x768"
    EndSubSection
EndSection[/PHP]

---

### Post by c00lryguy on 2009-09-10
I finally got it!

I had to add
[PHP]
    HorizSync        24-80
    VertRefresh      55-75
    DisplaySize     405.18 370.44
[/PHP]

to the "Monitor" section. Had to get my actual monitors specs to do so. =D Thanks for giving me a headstart on this though.

---

