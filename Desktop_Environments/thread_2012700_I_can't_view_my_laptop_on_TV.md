---
title: "I can't view my laptop on TV"
date: 2012-06-29
forum: Desktop Environments
---

### Post by salva99 on 2012-06-29
I have a Compaq c770 with an Intel graphic chipset. I'm running  Ubuntu 12.04. I plug the TV through a S-VIDEO port. However, nothing  appears on the TV.
Ubuntu detects the TV, and I can configure it. However, the TV is still black.


When I write ```
xrandr --verbose
``` it shows this:


```

TV1 connected 1024x768+1280+0 (0x4b) normal (normal left inverted right x axis y axis) 0mm x 0mm
Identifier: 0x43
Timestamp: 1262326
Subpixel: unknown
Gamma:      1.0:1.0:1.0 
Brightness: 1.0  
Clones:      
CRTC:       1  
CRTCs:      1 0  
Transform:  1.000000 0.000000 0.000000
              0.000000 1.000000 0.000000
              0.000000 0.000000 1.000000             
filter:   
bottom margin: 37 (0x00000025)  
range:  (0,100)  
right margin: 46 (0x0000002e)   
range:  (0,100)  
top margin: 36 (0x00000024) 
range:  (0,100)  
left margin: 54 (0x00000036)    
range:  (0,100)  
mode:   NTSC-M      
supported: NTSC-M       NTSC-443     NTSC-J       PAL-M                        PAL-N        PAL         

480p@59.94Hz 480p@60Hz                    576p         720p@60Hz    720p@59.94Hz 720p@50Hz                    1080i@50Hz   1080i@60Hz   1080i@59.94H 
848x480 (0x49) 29.0MHz +preferred
    h: width   848 start  849 end  912 total  944 skew    0 clock   30.7KHz      v: height  480 start  481 end  512 total  513           clock   59.9Hz 
640x480 (0x4a) 22.6MHz +preferred
    h: width   640 start  641 end  704 total  736 skew    0 clock   30.7KHz      v: height  480 start  481 end  512 total  513           clock   59.9Hz 
1024x768 (0x4b) 53.8MHz *current
    h: width  1024 start 1025 end 1088 total 1120 skew    0 clock   48.0KHz      v: height  768 start  769 end  800 total  801           clock   59.9Hz 
800x600 (0x4c) 34.0MHz
    h: width   800 start  801 end  864 total  896 skew    0 clock   37.9KHz      v: height  600 start  601 end  632 total  633           clock   59.9Hz 
```I'm booting up with the TV plugged. I'm plugging trough a s-video 8 pin --> scart cable.
It has an Intel® Graphics Media Accelerator X3100 graphic card.

I really don't know what is wrong.

---

### Post by salva99 on 2012-06-30
Could be a problem with the graphic card?

---

### Post by efflandt on 2012-06-30
What is the resolution of your laptop display?

I have not done that lately, but when I used to output an old laptop from y2k (Jan 2000) to TV, I could use up to 1024x768.   Or a VGA to TV converter would only work at 640x480. So try setting your laptop screen resolution to 1024x768 (or 640x480).

At least if mirroring your display I believe that laptop screen often has to be at same resolution as external display or projector (or modes that the external display accepts, if not native resolution).

---

### Post by salva99 on 2012-07-07
Thanks efflandt.
I'm not going to test it until two weeks because I'm not being home until then . When I test it, I'll reply .

---

### Post by salva99 on 2012-07-15
I've changed the resolution to 800x600
[IMG]http://ubuntuone.com/0Vu8dwvHD6Gg0FOxkh47eZ[/IMG]

I'm in Spain so the tv mode is PAL or PAL-N
```
xrandr --output TV1 --set mode PAL-N
xrandr --verbose
```[IMG]http://ubuntuone.com/59Vn2qPFiOBt4Zw6IyvTox[/IMG]


However, the tv still shows "Not signal"

---

### Post by skaarup90 on 2013-01-08
I have the same problem and I don't know it yet, if you find out plz text me or something :-)

---

